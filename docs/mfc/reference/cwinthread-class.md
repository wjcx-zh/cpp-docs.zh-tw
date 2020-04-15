---
title: CWinThread 類別
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367412"
---
# <a name="cwinthread-class"></a>CWinThread 類別

代表應用程式內執行的執行緒。

## <a name="syntax"></a>語法

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinThread:CWinThread](#cwinthread)|建構 `CWinThread` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinThread::建立線程](#createthread)|開始執行`CWinThread`物件。|
|[CWinThread:退出實例](#exitinstance)|重寫以線上程終止時清理。|
|[CWinThread:取得主菜](#getmainwnd)|檢索指向線程的主視窗的指標。|
|[CWinThread:取得線程優先順序](#getthreadpriority)|獲取當前線程的優先順序。|
|[CWinThread:inininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininin](#initinstance)|重寫以執行線程實例初始化。|
|[CWinThread::空閒消息](#isidlemessage)|檢查特殊消息。|
|[CWinThread:onidle](#onidle)|覆蓋以執行特定於線程的空閑時間處理。|
|[CWinThread::P奧斯特線程消息](#postthreadmessage)|將消息發佈到其他`CWinThread`物件。|
|[CWinThread::P重新翻譯消息](#pretranslatemessage)|在郵件發送到 Windows 函數[「翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)」和[「調度訊息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)」之前對其進行篩選。|
|[CWinThread::Process消息篩檢程式](#processmessagefilter)|在某些消息到達應用程式之前攔截它們。|
|[CWinThread::P羅塞斯·溫德普羅奇例外](#processwndprocexception)|攔截線程的消息和命令處理程序引發的所有未處理異常。|
|[CWinThread::Pump消息](#pumpmessage)|包含線程的消息迴圈。|
|[CWinThread:恢復線程](#resumethread)|取消線程的掛起計數。|
|[CWinThread:執行](#run)|使用消息泵控制螺紋的功能。 重寫以自定義預設消息迴圈。|
|[CWinThread::設置線程優先順序](#setthreadpriority)|設置當前線程的優先順序。|
|[CWinThread:暫停線程](#suspendthread)|增加線程的掛起計數。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CWinThread::操作員 HANDLE](#operator_handle)|檢索`CWinThread`物件的句柄。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CWinThread:m_bAutoDelete](#m_bautodelete)|指定是否線上程終止時銷毀物件。|
|[CWinThread:m_hThread](#m_hthread)|處理當前線程。|
|[CWinThread:m_nThreadID](#m_nthreadid)|當前線程的 ID。|
|[CWinThread:m_pActiveWnd](#m_pactivewnd)|當 OLE 伺服器就地處於活動狀態時,指向容器應用程式的主視窗。|
|[CWinThread:m_pMainWnd](#m_pmainwnd)|保存指向應用程式主視窗的指標。|

## <a name="remarks"></a>備註

執行的主線程通常由派生自`CWinApp`的物件提供。`CWinApp`派生自`CWinThread`。 其他`CWinThread`物件允許在給定應用程式中有多個線程。

`CWinThread`支援兩種常規類型的線程:工作線程和用戶介面線程。 工作線程沒有消息泵:例如,在電子錶格應用程式中執行後台計算的線程。 用戶介面線程具有消息泵和處理從系統接收的消息。 [CWinApp](../../mfc/reference/cwinapp-class.md)和派生自它的類是用戶介面線程的示例。 其他用戶介面線程也可以直接從`CWinThread`派生。

類`CWinThread`的物件通常存在於線程的持續時間內。 如果要修改此行為,請[將m_bAutoDelete](#m_bautodelete)設置為 FALSE。

要使`CWinThread`代碼和 MFC 完全線程安全,必須使用該類。 框架用於維護線程特定資訊的線程本地數據由`CWinThread`物件管理。 由於依賴`CWinThread`來處理線程本地數據,因此使用 MFC 的任何線程必須由 MFC 創建。 例如,執行時函數_beginthread創建的線程[,_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)無法使用任何 MFC API。

要建立線程,請致電[AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有兩種形式,具體取決於是需要輔助角色線程還是用戶介面線程。 如果需要用戶介面線程,請傳遞到`AfxBeginThread`指向`CRuntimeClass``CWinThread`派生類的指標。 如果要創建輔助線程,請傳遞到`AfxBeginThread`指向控制函數的指標以及指向控制函數的參數。 對於工作線程和使用者介面線程,可以指定修改優先順序、堆疊大小、創建標誌和安全屬性的可選參數。 `AfxBeginThread`將返回指向新`CWinThread`物件的指標。

可以建構`AfxBeginThread``CWinThread`派生物件,然後呼`CreateThread`叫 ,而不是呼叫 。 如果要在連續建立和線程執行終止之間重用該物件,`CWinThread`則此兩階段構造方法非常有用。

有關的詳細資訊`CWinThread`,請參閱[文章「使用 C++和 MFC 進行多線程」](../../parallel/multithreading-with-cpp-and-mfc.md),[多線程:建立使用者介面線程](../../parallel/multithreading-creating-user-interface-threads.md),[多線程:建立輔助線程](../../parallel/multithreading-creating-worker-threads.md)與[多線程:如何使用同步類](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::建立線程

創建要在調用進程的位址空間內執行的線程。

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>參數

*dwCreateFlags*<br/>
指定控制建立線程的其他標誌。 這個標誌可以包含兩個值之一:

- CREATE_SUSPENDED以1的掛起計數啟動線程。 如果要在線程開始運行之前初始化`CWinThread`物件的任何成員數據(如[m_bAutoDelete](#m_bautodelete)或派生類的任何成員,請使用CREATE_SUSPENDED。 初始化完成後,使用[CWinThread:resumeThread](#resumethread)開始線程運行。 在調用線程之前`CWinThread::ResumeThread`,線程不會執行。

- **0**創建後立即啟動線程。

*nStackSize*<br/>
指定新線程堆疊的大小(以位元組為單位)。 如果**為 0,** 則堆疊大小預設與行程主線程的大小相同。

*lpSecurityAttrs*<br/>
指向指定線程的安全屬性[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構。

### <a name="return-value"></a>傳回值

如果線程成功創建,則非零;否則 0。

### <a name="remarks"></a>備註

用於`AfxBeginThread`創建線程物件並在一個步驟中執行它。 如果要`CreateThread`在連續創建和終止線程執行之間重用線程物件,請使用。

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread:CWinThread

建構 `CWinThread` 物件。

```
CWinThread();
```

### <a name="remarks"></a>備註

要開始線程的執行,請調用[CreateThread](#createthread)成員函數。 您通常透過呼叫[AfxBeginThread](application-information-and-management.md#afxbeginthread)來建立線程,這將呼叫此建構`CreateThread`函數和 。

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread:退出實例

由框架從很少重寫[的 Run](#run)成員函數中調用以退出線程的此實例,或者如果對[InitInstance](#initinstance)的調用失敗。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>傳回值

線程的退出代碼;0 表示沒有錯誤,大於 0 的值表示錯誤。 可以通過調用[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)來檢索此值。

### <a name="remarks"></a>備註

不要從任何位置調用此成員函數,`Run`但不得在成員函數內調用。 此成員函數僅在用戶介面線程中使用。

如果`CWinThread`[m_bAutoDelete](#m_bautodelete)為 TRUE,則此函數的默認實現將刪除該物件。 如果要在線程終止時執行其他清理,請重寫此函數。 執行代碼後`ExitInstance`,應調用 基類的版本。

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread:取得主菜

如果應用程式是 OLE 伺服器,請呼叫此函式以檢索指向應用程式活動主視窗的指標,而不是直接引用應用程式`m_pMainWnd`物件的成員。

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>傳回值

此函數返回指向兩種類型的視窗之一的指標。 如果線程是 OLE 伺服器的一部分,並且物件在活動容器內處於活動狀態,則此函數`CWinThread`將返回 物件的[CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd)數據成員。

如果容器內沒有就地處於活動狀態的物件,或者您的應用程式不是 OLE 伺服器,則此函數將返回線程物件的[m_pMainWnd](#m_pmainwnd)數據成員。

### <a name="remarks"></a>備註

對於使用者介面線程,這相當於直接引用應用程式物件`m_pActiveWnd`的成員。

如果您的應用程式不是 OLE 伺服器，則呼叫此函式和直接參考應用程式物件的 `m_pMainWnd` 成員的功用相同。

重寫此函數以修改預設行為。

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread:取得線程優先順序

獲取此線程的當前線程優先順序級別。

```
int GetThreadPriority();
```

### <a name="return-value"></a>傳回值

其優先順序中的當前線程優先順序級別。 返回的值將是以下值之一,從最高優先順序列至最低優先順序:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

有關這些優先順序的詳細資訊,請參閱 Windows SDK 中的[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread:inininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininininin

`InitInstance`必須重寫才能初始化使用者介面線程的每個新實例。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

通常,您可以重寫`InitInstance`以執行在首次創建線程時必須完成的任務。

此成員函數僅在用戶介面線程中使用。 在傳遞給[AfxBeginThread](application-information-and-management.md#afxbeginthread)的控制函數中執行輔助線程的初始化。

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::空閒消息

重寫此函數以防止`OnIdle`在生成特定消息后被調用。

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向正在處理的當前消息。

### <a name="return-value"></a>傳回值

處理消息后`OnIdle`應調用非零;如果處理消息后應調用非零。否則 0。

### <a name="remarks"></a>備註

默認實現不會在冗餘滑鼠`OnIdle`消息和閃爍的 cares 生成的消息之後調用。

如果應用程式已創建短計時器,`OnIdle`將頻繁調用,從而導致性能問題。 為了提高此類應用程式的性能,請在應用程式的`IsIdleMessage``CWinApp`派生類中重寫以檢查WM_TIMER消息,如下所示:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

以這種方式處理WM_TIMER將提高使用短計時器的應用程式的性能。

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread:m_bAutoDelete

指定在執行緒終止時是否要自動刪除 `CWinThread` 物件。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>備註

數據`m_bAutoDelete`成員是 BOOL 類型的公共變數。

的值`m_bAutoDelete`不會影響基礎線程句柄的關閉方式,但它確實會影響關閉句柄的時間。 在 `CWinThread` 物件終結時，執行緒控制代碼永遠關閉。

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread:m_hThread

處理附加到此`CWinThread`的線程。

```
HANDLE m_hThread;
```

### <a name="remarks"></a>備註

數據`m_hThread`成員是 HANDLE 類型的公共變數。 僅當基礎內核線程物件當前存在且句柄尚未關閉時,它才有效。

CWinThread 析構函數調用`m_hThread`上的 CloseHandle。 如果[當](#m_bautodelete)線程終止時m_bAutoDelete為 TRUE,則 CWinThread 物件將被銷毀,從而使指向 CWinThread 物件及其成員變數的任何指標無效。 您可能需要成員`m_hThread`檢查線程退出值,或等待信號。 要線上程執行期間和終止後保留`m_hThread`CWinThread 物件及其成員,請`m_bAutoDelete`設置為 FALSE,然後再允許線程執行繼續。 否則,線程可能會終止、銷毀 CWinThread 物件,並在嘗試使用它之前關閉句柄。 如果使用此技術,則負責刪除 CWinThread 物件。

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread:m_nThreadID

附加到此`CWinThread`的線程的 ID。

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>備註

數據`m_nThreadID`成員是 DWORD 類型的公共變數。 僅當基礎內核線程物件當前存在時,它才有效。
另請參閱有關[m_hThread](#m_hthread)存留期的評論。

### <a name="example"></a>範例

  請參閱[AfxGetThread](application-information-and-management.md#afxgetthread)的範例。

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread:m_pActiveWnd

使用此數據成員可以儲存指向線程活動視窗物件的指標。

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>備註

當引用`m_pActiveWnd`的窗口關閉時,Microsoft 基礎類庫將自動終止線程。 如果此線程是應用程式的主線程,則應用程式也將終止。 如果此資料成員為 NULL,則將繼承`CWinApp`應用程式 物件的活動視窗。 `m_pActiveWnd`是類型的`CWnd*`公共變數。

通常,在重寫`InitInstance`時設置此成員變數。 在輔助線程中,此數據成員的值從其父線程繼承。

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread:m_pMainWnd

使用此數據成員可以儲存指向線程主視窗物件的指標。

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>備註

當引用`m_pMainWnd`的窗口關閉時,Microsoft 基礎類庫將自動終止線程。 如果此線程是應用程式的主線程,則應用程式也將終止。 如果此資料成員為 NULL,則`CWinApp`應用程式 物件的主視窗將用於確定何時終止線程。 `m_pMainWnd`是類型的`CWnd*`公共變數。

通常,在重寫`InitInstance`時設置此成員變數。 在輔助線程中,此數據成員的值從其父線程繼承。

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread:onidle

重寫此成員函數以執行空閒時間處理。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>參數

*l. Count*<br/>
當線程的消息隊列為空`OnIdle`時,每次調用一個計數器。 每次處理新消息時,此計數都會重置為 0。 可以使用*lCount*參數來確定線程空閒的相對時間長度,而無需處理消息。

### <a name="return-value"></a>傳回值

非零接收更多的空閒處理時間;如果不需要更多的空閒處理時間,則為 0。

### <a name="remarks"></a>備註

`OnIdle`當線程的消息隊列為空時,在預設消息迴圈中調用。 使用重寫呼叫您自己的後台空閒處理程式任務。

`OnIdle`應返回 0 以指示不需要額外的空閒處理時間。 每次`OnIdle`在消息隊列為空時調用*lCount*參數都會增加,並且每次處理新消息時都重置為 0。 您可以基於此計數調用不同的空閒例程。

此成員函數的預設實現將臨時物件和未使用的動態連結庫從記憶體中釋放。

此成員函數僅在用戶介面線程中使用。

由於應用程式無法處理消息,直到`OnIdle`返回,因此不要在此函數中執行冗長的任務。

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::操作員 HANDLE

檢索`CWinThread`物件的句柄。

```
operator HANDLE() const;
```

### <a name="return-value"></a>傳回值

如果成功,線程物件的句柄;否則,NULL。

### <a name="remarks"></a>備註

使用該句柄直接調用 Windows API。

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::P奧斯特線程消息

調用以將使用者定義的消息發佈到其他`CWinThread`物件。

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*訊息*<br/>
使用者定義消息的 ID。

*wParam*<br/>
第一個消息參數。

*lParam*<br/>
第二個消息參數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

消息映射宏ON_THREAD_MESSAGE將發佈的消息映射到正確的消息處理程式。

> [!NOTE]
> 當您調用[PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)時,消息將放置在線程的消息佇列中。 但是,由於以這種方式發佈的消息不與窗口關聯,MFC 不會將它們調度到消息或命令處理程式。 為了處理這些消息,請重寫`PreTranslateMessage()`CWinApp 派生類的功能,並手動處理消息。

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::P重新翻譯消息

重寫此函數以篩選視窗訊息,然後再將其傳送到 Windows 函數[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[排程訊息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
包含要處理的[MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)。

### <a name="return-value"></a>傳回值

如果消息已完全處理,`PreTranslateMessage`則非零,不應進一步處理。 如果消息應以正常方式處理,則為零。

### <a name="remarks"></a>備註

此成員函數僅在用戶介面線程中使用。

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::Process消息篩檢程式

框架的 hook 函數呼叫此成員函數來篩選和回應某些 Windows 訊息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*代碼*<br/>
指定挂鉤代碼。 此成員函數使用代碼來確定如何處理*lpMsg。*

*lpMsg*<br/>
指向 Windows [MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)的指標。

### <a name="return-value"></a>傳回值

處理消息時非零;否則 0。

### <a name="remarks"></a>備註

hook 函數在事件發送到應用程式的正常消息處理之前處理事件。

如果重寫此高級功能,請確保調用基類版本以維護框架的挂鉤處理。

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::P羅塞斯·溫德普羅奇例外

每當處理程式不捕獲線程的消息或命令處理程序中引發異常時,框架將調用此成員函數。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>參數

*e*<br/>
指向未處理的異常。

*pMsg*<br/>
包含與包含或框架的視窗訊息的[MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)。

### <a name="return-value"></a>傳回值

-1 如果生成WM_CREATE異常;如果生成異常,則為 -1;否則 0。

### <a name="remarks"></a>備註

不要直接調用此成員函數。

此成員函數的預設實現僅處理以下訊息產生的異常:

|Command|動作|
|-------------|------------|
|WM_CREATE|失敗。|
|WM_PAINT|驗證受影響的視窗,從而阻止生成另一WM_PAINT消息。|

重寫此成員函數,以提供異常的全域處理。 僅當希望顯示默認行為時,才調用基本功能。

此成員函數僅在具有消息泵的線程中使用。

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::Pump消息

包含線程的消息迴圈。

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>備註

`PumpMessage`包含線程的消息迴圈。 `PumpMessage`調用`CWinThread`以 泵送線程的消息。 您可以直接呼叫`PumpMessage`以強制處理郵件,也可以重`PumpMessage`寫 以更改其預設行為。

建議`PumpMessage`僅對高級使用者直接調用並重寫其默認行為。

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread:恢復線程

調用 以恢復執行由[掛起Thread](#suspendthread)成員函數掛起的線程,或使用 CREATE_SUSPENDED 標誌創建的線程。

```
DWORD ResumeThread();
```

### <a name="return-value"></a>傳回值

線程以前的掛起計數(如果成功);`0xFFFFFFFF`否則。 如果返回值為零,則當前線程未掛起。 如果返回值為 1,則線程已掛起,但現在重新啟動。 任何大於 1 的返回值都意味著線程將保持掛起狀態。

### <a name="remarks"></a>備註

當前線程的掛起計數減少 1。 如果掛起計數減少到零,線程將恢復執行;如果掛起計數減少到零,則線程將恢復執行。否則,線程將保持掛起狀態。

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread:執行

為使用者介面線程提供預設消息迴圈。

```
virtual int Run();
```

### <a name="return-value"></a>傳回值

線程返回的**int**值。 可以通過調用[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)來檢索此值。

### <a name="remarks"></a>備註

`Run`獲取和調度 Windows 消息,直到應用程式收到[WM_QUIT](/windows/win32/winmsg/wm-quit)消息。 如果線程的消息佇列當前不包含任何消息,則`Run`調用`OnIdle`以執行空閑時間處理。 傳入訊息轉到[PreTranslateMessage](#pretranslatemessage)成員函數進行特殊處理,然後轉到 Windows 函數[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)進行標準鍵盤翻譯。 最後,調用[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗函數。

`Run`很少重寫,但您可以重寫它以實現特殊行為。

此成員函數僅在用戶介面線程中使用。

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::設置線程優先順序

此函數在其優先順序類中設置當前線程的優先順序。

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>參數

*n優先*<br/>
在其優先順序類中指定新的線程優先順序級別。 此參數必須是以下值之一,從最高優先順序列至最低優先順序:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

有關這些優先順序的詳細資訊,請參閱 Windows SDK 中的[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

只能在[CreateThread](#createthread)成功返回後調用它。

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread:暫停線程

增加當前線程的掛起計數。

```
DWORD SuspendThread();
```

### <a name="return-value"></a>傳回值

線程以前的掛起計數(如果成功);`0xFFFFFFFF`否則。

### <a name="remarks"></a>備註

如果任何線程的掛起計數高於零,則該線程不會執行。 可以通過調用[ResumeThread](#resumethread)成員函數來恢復線程。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
