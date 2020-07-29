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
ms.openlocfilehash: 6dbe4c4d3ed5edaf0563abf589cd844cca6803f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182768"
---
# <a name="cwinthread-class"></a>CWinThread 類別

代表應用程式內執行的執行緒。

## <a name="syntax"></a>語法

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CWinThread：： CWinThread](#cwinthread)|建構 `CWinThread` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CWinThread：： CreateThread](#createthread)|開始執行 `CWinThread` 物件。|
|[CWinThread：： ExitInstance](#exitinstance)|當您的執行緒終止時，覆寫以進行清除。|
|[CWinThread：： GetMainWnd](#getmainwnd)|抓取執行緒主視窗的指標。|
|[CWinThread：： GetThreadPriority](#getthreadpriority)|取得目前線程的優先順序。|
|[CWinThread：： InitInstance](#initinstance)|覆寫以執行執行緒實例初始化。|
|[CWinThread：： IsIdleMessage](#isidlemessage)|檢查是否有特殊訊息。|
|[CWinThread：： OnIdle](#onidle)|覆寫以執行執行緒特定的閒置時間處理。|
|[CWinThread：:P ostThreadMessage](#postthreadmessage)|將訊息張貼至另一個 `CWinThread` 物件。|
|[CWinThread：:P reTranslateMessage](#pretranslatemessage)|在訊息分派至 Windows 函式[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)之前，先進行篩選。|
|[CWinThread：:P rocessMessageFilter](#processmessagefilter)|攔截特定訊息，然後再到達應用程式。|
|[CWinThread：:P rocessWndProcException](#processwndprocexception)|攔截由執行緒的訊息和命令處理常式擲回的所有未處理的例外狀況。|
|[CWinThread：:P umpMessage](#pumpmessage)|包含執行緒的訊息迴圈。|
|[CWinThread：： ResumeThread](#resumethread)|遞減執行緒的暫停計數。|
|[CWinThread：： Run](#run)|使用訊息抽取控制執行緒的函式。 覆寫以自訂預設訊息迴圈。|
|[CWinThread：： SetThreadPriority](#setthreadpriority)|設定目前線程的優先順序。|
|[CWinThread：： SuspendThread](#suspendthread)|遞增執行緒的暫停計數。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CWinThread：： operator 控制碼](#operator_handle)|抓取物件的控制碼 `CWinThread` 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CWinThread：： m_bAutoDelete](#m_bautodelete)|指定是否要線上程終止時終結物件。|
|[CWinThread：： m_hThread](#m_hthread)|目前線程的控制碼。|
|[CWinThread：： m_nThreadID](#m_nthreadid)|目前線程的識別碼。|
|[CWinThread：： m_pActiveWnd](#m_pactivewnd)|當 OLE 伺服器為就地作用中時，容器應用程式主視窗的指標。|
|[CWinThread：： m_pMainWnd](#m_pmainwnd)|保存應用程式主視窗的指標。|

## <a name="remarks"></a>備註

執行的主要執行緒通常是由衍生自的物件所提供 `CWinApp` ; `CWinApp` 衍生自 `CWinThread` 。 其他 `CWinThread` 物件允許在指定的應用程式內使用多個執行緒。

支援的一般執行緒類型有兩種 `CWinThread` ：背景工作執行緒和使用者介面執行緒。 工作者執行緒沒有訊息提取：例如，在試算表應用程式中執行背景計算的執行緒。 使用者介面執行緒具有訊息抽取，並處理從系統接收的訊息。 [CWinApp](../../mfc/reference/cwinapp-class.md)和衍生自它的類別是使用者介面執行緒的範例。 其他使用者介面執行緒也可以直接從衍生 `CWinThread` 。

類別的物件 `CWinThread` 通常存在於執行緒的持續時間內。 如果您想要修改此行為，請將[m_bAutoDelete](#m_bautodelete)設定為 FALSE。

`CWinThread`必須要有類別，才能讓您的程式碼和 MFC 具備完全安全線程。 架構用來維護執行緒特定資訊的執行緒區域資料是由物件所管理 `CWinThread` 。 由於此相依性 `CWinThread` 會處理執行緒區域資料，因此任何使用 mfc 的執行緒都必須由 mfc 建立。 例如，執行時間函數所建立的執行緒[_beginthread，_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)無法使用任何 MFC api。

若要建立執行緒，請呼叫[AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有兩種形式，視您是否想要背景工作角色或使用者介面執行緒而定。 如果您想要使用者介面執行緒，請傳遞至 `AfxBeginThread` `CRuntimeClass` 衍生類別之的指標 `CWinThread` 。 如果您想要建立背景工作執行緒，請傳遞至控制函式 `AfxBeginThread` 和參數的指標至控制函數。 對於背景工作執行緒和使用者介面執行緒，您可以指定修改優先順序、堆疊大小、建立旗標和安全性屬性的選擇性參數。 `AfxBeginThread`會傳回新物件的指標 `CWinThread` 。

除了呼叫之外 `AfxBeginThread` ，您還可以先建立 `CWinThread` 衍生的物件，然後再呼叫 `CreateThread` 。 如果您想要在 `CWinThread` 執行緒執行的連續建立和終止之間重複使用物件，這個兩階段的結構方法會很有用。

如需有關的詳細資訊 `CWinThread` ，請參閱[使用 c + + 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)文章、[多執行緒：建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)、[多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)和[多執行緒：如何使用同步處理類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread：： CreateThread

建立要在呼叫進程的位址空間內執行的執行緒。

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>參數

*dwCreateFlags*<br/>
指定控制執行緒建立的其他旗標。 此旗標可以包含兩個值的其中一個：

- CREATE_SUSPENDED 啟動暫停計數為1的執行緒。 如果您想要線上程開始執行之前初始化物件的任何成員資料 `CWinThread` ，例如[m_bAutoDelete](#m_bautodelete)或衍生類別的任何成員，請使用 CREATE_SUSPENDED。 一旦初始化完成之後，請使用[CWinThread：： ResumeThread](#resumethread)來啟動執行的執行緒。 在呼叫之前，執行緒將不會執行 `CWinThread::ResumeThread` 。

- **0**在建立之後立即啟動執行緒。

*nStackSize*<br/>
指定新執行緒的堆疊大小（以位元組為單位）。 如果是**0**，堆疊大小會預設為與進程的主要執行緒相同的大小。

*lpSecurityAttrs*<br/>
指向指定執行緒之安全性屬性的[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構。

### <a name="return-value"></a>傳回值

如果成功建立執行緒，則為非零;否則為0。

### <a name="remarks"></a>備註

使用 `AfxBeginThread` 建立 thread 物件，並在一個步驟中執行。 `CreateThread`如果您想要在連續建立和終止執行緒執行之間重複使用 thread 物件，請使用。

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread：： CWinThread

建構 `CWinThread` 物件。

```
CWinThread();
```

### <a name="remarks"></a>備註

若要開始執行緒的執行，請呼叫[CreateThread](#createthread)成員函式。 您通常會藉由呼叫[AfxBeginThread](application-information-and-management.md#afxbeginthread)來建立執行緒，這會呼叫這個函式和 `CreateThread` 。

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread：： ExitInstance

由架構從很少覆寫的[執行](#run)成員函式中呼叫，以結束此執行緒的實例，或呼叫[InitInstance](#initinstance)失敗。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>傳回值

執行緒的結束代碼;0表示沒有錯誤，而大於0的值表示發生錯誤。 呼叫[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)可以抓取此值。

### <a name="remarks"></a>備註

請勿在成員函式內的任何位置呼叫此成員函式 `Run` 。 這個成員函式僅適用于使用者介面執行緒。

`CWinThread`如果[M_BAUTODELETE](#m_bautodelete)為 TRUE，此函式的預設實作用會刪除物件。 如果您想要線上程終止時執行其他清除工作，請覆寫此函式。 `ExitInstance`執行程式碼之後，您的執行應該會呼叫基類的版本。

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread：： GetMainWnd

如果您的應用程式是 OLE 伺服器，請呼叫此函式來抓取應用程式之作用中主視窗的指標，而不是直接參考 `m_pMainWnd` 應用程式物件的成員。

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>傳回值

此函式會傳回兩種視窗類型之一的指標。 如果您的執行緒是 OLE 伺服器的一部分，而且在作用中容器內有一個就地作用中的物件，此函式會傳回物件的[CWinApp：： m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd)資料成員 `CWinThread` 。

如果容器中沒有任何就地作用中的物件，或者您的應用程式不是 OLE 伺服器，則此函式會傳回 thread 物件的[m_pMainWnd](#m_pmainwnd)資料成員。

### <a name="remarks"></a>備註

對於使用者介面執行緒，這相當於直接參考 `m_pActiveWnd` 應用程式物件的成員。

如果您的應用程式不是 OLE 伺服器，則呼叫此函式和直接參考應用程式物件的 `m_pMainWnd` 成員的功用相同。

覆寫此函式以修改預設行為。

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread：： GetThreadPriority

取得此執行緒的目前線程優先權層級。

```
int GetThreadPriority();
```

### <a name="return-value"></a>傳回值

其優先順序類別內的目前線程優先權層級。 傳回的值將會是下列其中一項，列出從最高優先順序到最低：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

如需這些優先順序的詳細資訊，請參閱 Windows SDK 中的[SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread：： InitInstance

`InitInstance`必須覆寫，才能初始化使用者介面執行緒的每個新實例。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為0。

### <a name="remarks"></a>備註

一般而言，您會覆寫 `InitInstance` 以執行必須在第一次建立執行緒時完成的工作。

這個成員函式僅適用于使用者介面執行緒。 在傳遞至[AfxBeginThread](application-information-and-management.md#afxbeginthread)的控制函數中，執行背景工作執行緒的初始化。

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread：： IsIdleMessage

覆寫此函式，使其 `OnIdle` 不會在產生特定訊息之後被呼叫。

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向目前正在處理的訊息。

### <a name="return-value"></a>傳回值

如果 `OnIdle` 應該在處理訊息後呼叫，則為非零，否則為0。

### <a name="remarks"></a>備註

預設的執行不會 `OnIdle` 在重複的滑鼠訊息和由閃爍的插入號所產生的訊息之後呼叫。

如果應用程式已建立短暫的計時器， `OnIdle` 則會經常呼叫，而造成效能問題。 若要改善這類應用程式的效能，請 `IsIdleMessage` 在應用程式的衍生類別中覆寫 `CWinApp` 以檢查 WM_TIMER 訊息，如下所示：

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

以這種方式處理 WM_TIMER 將會改善使用短暫計時器之應用程式的效能。

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread：： m_bAutoDelete

指定在執行緒終止時是否要自動刪除 `CWinThread` 物件。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>備註

`m_bAutoDelete`資料成員是 BOOL 類型的公用變數。

的值 `m_bAutoDelete` 不會影響基礎執行緒控制碼的關閉方式，但它會影響關閉控制碼的時機。 在 `CWinThread` 物件終結時，執行緒控制代碼永遠關閉。

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread：： m_hThread

附加至這個之執行緒的控制碼 `CWinThread` 。

```
HANDLE m_hThread;
```

### <a name="remarks"></a>備註

`m_hThread`資料成員是 HANDLE 類型的公用變數。 只有在基礎核心執行緒物件目前存在，而且控制碼尚未關閉時，才會有效。

CWinThread 析構函式會呼叫上的 CloseHandle `m_hThread` 。 如果[m_bAutoDelete](#m_bautodelete)線上程終止時為 TRUE，則會終結 CWinThread 物件，這會使 CWinThread 物件及其成員變數的任何指標失效。 您可能需要 `m_hThread` 成員來檢查執行緒結束值，或等候信號。 若要 `m_hThread` 線上程執行期間及終止之後保留 CWinThread 物件及其成員，請將設定 `m_bAutoDelete` 為 FALSE，然後才允許執行緒繼續執行。 否則，執行緒可能會終止、終結 CWinThread 物件，並在您嘗試使用該控制碼之前先關閉它。 如果您使用這項技術，就必須負責刪除 CWinThread 物件。

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread：： m_nThreadID

附加至此的執行緒識別碼 `CWinThread` 。

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>備註

`m_nThreadID`資料成員是 DWORD 類型的公用變數。 只有在基礎核心執行緒物件目前存在時，它才有效。
另請參閱關於[m_hThread](#m_hthread)存留期的備註。

### <a name="example"></a>範例

  請參閱[AfxGetThread](application-information-and-management.md#afxgetthread)的範例。

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread：： m_pActiveWnd

使用此資料成員，將指標儲存至執行緒的使用中視窗物件。

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>備註

當所參考的視窗已關閉時，MFC 程式庫會自動終止您的執行緒 `m_pActiveWnd` 。 如果這個執行緒是應用程式的主要執行緒，應用程式也會終止。 如果此資料成員為 Null，則會繼承應用程式物件的使用中視窗 `CWinApp` 。 `m_pActiveWnd`是類型的公用變數 `CWnd*` 。

一般來說，您會在覆寫時設定這個成員變數 `InitInstance` 。 在背景工作執行緒中，此資料成員的值會繼承自其父執行緒。

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread：： m_pMainWnd

使用此資料成員來儲存執行緒的主視窗物件指標。

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>備註

當所參考的視窗已關閉時，MFC 程式庫會自動終止您的執行緒 `m_pMainWnd` 。 如果這個執行緒是應用程式的主要執行緒，應用程式也會終止。 如果此資料成員為 Null，則會使用應用程式物件的主視窗 `CWinApp` 來判斷何時終止執行緒。 `m_pMainWnd`是類型的公用變數 `CWnd*` 。

一般來說，您會在覆寫時設定這個成員變數 `InitInstance` 。 在背景工作執行緒中，此資料成員的值會繼承自其父執行緒。

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread：： OnIdle

覆寫此成員函式以執行閒置時間處理。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>參數

*lCount*<br/>
`OnIdle`當執行緒的訊息佇列是空的時，每次呼叫時，就會遞增計數器。 每次處理新訊息時，此計數就會重設為0。 您可以使用*lCount*參數來判斷線程閒置而不處理訊息的相對時間長度。

### <a name="return-value"></a>傳回值

非零以接收更多閒置處理時間;如果不再需要閒置處理時間，則為0。

### <a name="remarks"></a>備註

`OnIdle`當執行緒的訊息佇列是空的時，會在預設訊息迴圈中呼叫。 使用您的覆寫來呼叫您自己的背景閒置處理常式工作。

`OnIdle`應傳回0，表示不需要額外的閒置處理時間。 每*lCount*次 `OnIdle` 呼叫訊息佇列是空的時，lCount 參數會遞增，而且每次處理新訊息時，都會重設為0。 您可以根據此計數來呼叫不同的閒置常式。

此成員函式的預設執行會從記憶體中釋出暫存物件和未使用的動態連結程式庫。

這個成員函式僅適用于使用者介面執行緒。

因為應用程式在傳回之前無法處理訊息 `OnIdle` ，所以請勿在此函式中執行冗長的工作。

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread：： operator 控制碼

抓取物件的控制碼 `CWinThread` 。

```
operator HANDLE() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為執行緒物件的控制碼;否則為 Null。

### <a name="remarks"></a>備註

使用控制碼直接呼叫 Windows Api。

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread：:P ostThreadMessage

呼叫以將使用者定義的訊息張貼至另一個 `CWinThread` 物件。

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*message*<br/>
使用者自訂訊息的識別碼。

*wParam*<br/>
第一個訊息參數。

*lParam*<br/>
第二個訊息參數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

訊息對應宏 ON_THREAD_MESSAGE 會將張貼的訊息對應至適當的訊息處理常式。

> [!NOTE]
> 當您呼叫[PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)時，訊息會放線上程的訊息佇列中。 不過，由於以這種方式張貼的訊息不會與視窗相關聯，因此 MFC 不會將它們分派至訊息或命令處理常式。 為了處理這些訊息，請覆寫 `PreTranslateMessage()` CWinApp 衍生類別的函式，並手動處理訊息。

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread：:P reTranslateMessage

覆寫此函式以在分派至 Windows 函式[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)之前篩選視窗訊息。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向包含要處理之訊息的[MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)。

### <a name="return-value"></a>傳回值

如果訊息在中完整處理，則 `PreTranslateMessage` 不應進一步處理。 如果應該以正常方式處理訊息，則為零。

### <a name="remarks"></a>備註

這個成員函式僅適用于使用者介面執行緒。

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread：:P rocessMessageFilter

架構的攔截函式會呼叫這個成員函式來篩選和回應特定的 Windows 訊息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*code*<br/>
指定勾點碼。 此成員函式會使用程式碼來判斷如何處理*lpMsg。*

*lpMsg*<br/>
Windows [MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)的指標。

### <a name="return-value"></a>傳回值

如果已處理訊息，則為非零值;否則為0。

### <a name="remarks"></a>備註

攔截函式會在事件傳送至應用程式的一般訊息處理之前，先處理它們。

如果您覆寫這個先進的功能，請務必呼叫基類版本來維護架構的攔截處理。

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread：:P rocessWndProcException

每當處理常式未攔截到其中一個執行緒訊息或命令處理常式中擲回的例外狀況時，架構就會呼叫這個成員函式。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>參數

*版*<br/>
指向未處理的例外狀況。

*pMsg*<br/>
指向訊息[結構](/windows/win32/api/winuser/ns-winuser-msg)，其中包含導致架構擲回例外狀況之 windows 訊息的相關資訊。

### <a name="return-value"></a>傳回值

如果產生 WM_CREATE 例外狀況，則為-1;否則為0。

### <a name="remarks"></a>備註

請勿直接呼叫此成員函式。

這個成員函式的預設實作用只會處理從下列訊息產生的例外狀況：

|命令|動作|
|-------------|------------|
|WM_CREATE|失敗。|
|WM_PAINT|驗證受影響的視窗，以防止產生另一個 WM_PAINT 訊息。|

覆寫這個成員函式，以提供例外狀況的全域處理。 只有在您想要顯示預設行為時，才呼叫基底功能。

這個成員函式僅適用于具有訊息提取的執行緒。

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread：:P umpMessage

包含執行緒的訊息迴圈。

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>備註

`PumpMessage`包含執行緒的訊息迴圈。 `PumpMessage`會呼叫 `CWinThread` 來提取執行緒的訊息。 您可以 `PumpMessage` 直接呼叫來強制處理訊息，或者您可以覆寫 `PumpMessage` 以變更其預設行為。

`PumpMessage`建議您直接呼叫並覆寫其預設行為，僅供 advanced 使用者使用。

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread：： ResumeThread

呼叫以繼續執行[SuspendThread](#suspendthread)成員函式所暫止的執行緒，或使用 CREATE_SUSPENDED 旗標建立的執行緒。

```
DWORD ResumeThread();
```

### <a name="return-value"></a>傳回值

如果成功，則為執行緒先前的暫停計數;`0xFFFFFFFF`否則為。 如果傳回值為零，則不會暫止目前的執行緒。 如果傳回值為1，則執行緒已暫止，但現在已重新開機。 任何大於1的傳回值表示執行緒會保持暫停。

### <a name="remarks"></a>備註

目前線程的暫停計數會減一。 如果暫停計數縮減為零，則執行緒會繼續執行;否則，執行緒會保持暫止狀態。

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread：： Run

提供使用者介面執行緒的預設訊息迴圈。

```
virtual int Run();
```

### <a name="return-value"></a>傳回值

**`int`** 執行緒所傳回的值。 呼叫[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)可以抓取此值。

### <a name="remarks"></a>備註

`Run`取得和分派 Windows 訊息，直到應用程式收到[WM_QUIT](/windows/win32/winmsg/wm-quit)訊息為止。 如果執行緒的訊息佇列目前未包含任何訊息，則會 `Run` 呼叫 `OnIdle` 來執行閒置時間處理。 傳入的訊息會移至[PreTranslateMessage](#pretranslatemessage)成員函式進行特殊處理，然後傳送至 Windows 函式[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)進行標準鍵盤轉譯。 最後，會呼叫[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。

`Run`很少遭到覆寫，但是您可以覆寫它來執行特殊行為。

這個成員函式僅適用于使用者介面執行緒。

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread：： SetThreadPriority

此函式會設定其優先順序類別內目前線程的優先權層級。

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>參數

*nPriority*<br/>
指定其優先順序類別內的新執行緒優先權層級。 這個參數必須是下列其中一個值，從最高優先順序列出到最低：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

如需這些優先順序的詳細資訊，請參閱 Windows SDK 中的[SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零值;否則為0。

### <a name="remarks"></a>備註

只有在[CreateThread](#createthread)成功傳回之後，才能呼叫它。

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread：： SuspendThread

遞增目前線程的暫停計數。

```
DWORD SuspendThread();
```

### <a name="return-value"></a>傳回值

如果成功，則為執行緒先前的暫停計數;`0xFFFFFFFF`否則為。

### <a name="remarks"></a>備註

如果有任何執行緒的暫止計數超過零，該執行緒就不會執行。 您可以藉由呼叫[ResumeThread](#resumethread)成員函式來繼續執行執行緒。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
