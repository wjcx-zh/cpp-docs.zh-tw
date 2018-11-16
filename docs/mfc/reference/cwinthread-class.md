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
ms.openlocfilehash: 0f6c41b3675251df6b07e44003215fa67fb7e795
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694188"
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
|[CWinThread::CWinThread](#cwinthread)|建構 `CWinThread` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|開始執行`CWinThread`物件。|
|[CWinThread::ExitInstance](#exitinstance)|覆寫您的執行緒終止時清除。|
|[CWinThread::GetMainWnd](#getmainwnd)|擷取執行緒的主視窗的指標。|
|[CWinThread::GetThreadPriority](#getthreadpriority)|取得目前執行緒的優先權。|
|[CWinThread::InitInstance](#initinstance)|覆寫以執行執行緒的執行個體初始化。|
|[CWinThread::IsIdleMessage](#isidlemessage)|檢查特殊訊息。|
|[CWinThread::OnIdle](#onidle)|覆寫以執行特定執行緒的閒置時間處理。|
|[CWinThread::PostThreadMessage](#postthreadmessage)|將訊息張貼至另一個`CWinThread`物件。|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|篩選訊息，再將它們分派至 Windows 函式[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)。|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|到達應用程式之前，會攔截特定訊息。|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|攔截所有執行緒的訊息和命令處理常式所擲回的未處理例外狀況。|
|[CWinThread::PumpMessage](#pumpmessage)|包含執行緒的訊息迴圈。|
|[Cwinthread:: Resumethread](#resumethread)|遞減執行緒的暫停計數。|
|[Cwinthread:: Run](#run)|使用訊息幫浦執行緒的控制函式。 若要自訂預設訊息迴圈會覆寫。|
|[CWinThread::SetThreadPriority](#setthreadpriority)|設定目前執行緒的優先權。|
|[CWinThread::SuspendThread](#suspendthread)|增加的執行緒的暫停計數。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CWinThread::operator 控制代碼](#operator_handle)|擷取的控制代碼`CWinThread`物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|指定是否要終結的物件在執行緒終止。|
|[CWinThread::m_hThread](#m_hthread)|目前執行緒的控制代碼。|
|[CWinThread::m_nThreadID](#m_nthreadid)|目前執行緒的識別碼。|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|OLE 伺服器時就地啟用作用中的容器應用程式的主視窗的指標。|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|保留應用程式的主視窗的指標。|

## <a name="remarks"></a>備註

執行主執行緒通常透過衍生自物件提供`CWinApp`;`CWinApp`衍生自`CWinThread`。 其他`CWinThread`物件允許指定的應用程式內的多個執行緒。

有兩種一般的執行緒，`CWinThread`支援： 背景工作執行緒與使用者介面執行緒。 背景工作執行緒會有任何訊息幫浦： 例如，在試算表應用程式中執行背景計算的執行緒。 使用者介面執行緒擁有訊息幫浦，並處理從系統接收的訊息。 [CWinApp](../../mfc/reference/cwinapp-class.md)和從它衍生的類別是使用者介面執行緒的範例。 其他使用者介面執行緒也可以直接從衍生`CWinThread`。

類別的物件`CWinThread`通常存在之執行緒的持續時間。 如果您想要修改此行為，設定[create_suspended](#m_bautodelete)為 FALSE。

`CWinThread`類別是為了讓您的程式碼及 MFC 完整的安全執行緒。 維護執行緒特定的資訊架構所使用的執行緒區域資料由管理`CWinThread`物件。 因為此相依性`CWinThread`處理執行緒區域資料，任何使用 MFC 的執行緒必須由 MFC。 比方說，將執行階段函式所建立的執行緒[_beginthread、 _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)不能使用任何 MFC Api。

若要建立的執行緒，呼叫[AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有兩種形式，取決於您是在背景工作角色或使用者介面執行緒。 如果您想在使用者介面執行緒，將傳遞給`AfxBeginThread`的指標`CRuntimeClass`的您`CWinThread`-衍生的類別。 如果您想要建立的工作者執行緒，將傳遞給`AfxBeginThread`控制函式與參數來控制函式的指標。 背景工作執行緒和使用者介面執行緒中，您可以指定修改優先順序、 堆疊大小，建立旗標，以及安全性屬性的選擇性參數。 `AfxBeginThread` 會將指標傳回至新`CWinThread`物件。

而不是呼叫`AfxBeginThread`，您可以建構`CWinThread`-衍生物件，然後再呼叫`CreateThread`。 如果您想要重複使用這個兩階段建構方法相當實用`CWinThread`後續建立與終止的執行緒執行之間的物件。

如需詳細資訊`CWinThread`，請參閱文章[多執行緒 c + + 和 MFC](../../parallel/multithreading-with-cpp-and-mfc.md)，[多執行緒： 建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)，[多執行緒： 建立背景工作角色執行緒](../../parallel/multithreading-creating-worker-threads.md)，並[多執行緒： 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="createthread"></a>  CWinThread::CreateThread

建立執行緒來執行呼叫處理序位址空間內。

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>參數

*dwCreateFlags*<br/>
指定其他旗標控制執行緒的建立。 這個旗標可以包含兩個值之一：

- CREATE_SUSPENDED 啟動執行緒以暫停計數之一。 如果您想要初始化的任何成員資料，請使用 CREATE_SUSPENDED`CWinThread`物件，例如[create_suspended](#m_bautodelete)或衍生類別中，執行緒開始執行之前的任何成員。 您的初始化完成之後，使用[cwinthread:: Resumethread](#resumethread)開始執行的執行緒。 執行緒將不會執行直到`CWinThread::ResumeThread`呼叫。

- **0**在建立後立即啟動執行緒。

*nStackSize*<br/>
指定的大小，以位元組為單位的新執行緒的堆疊。 如果**0**，堆疊大小預設為與處理程序的主要執行緒的大小相同。

*lpSecurityAttrs*<br/>
指向[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定執行緒的安全性屬性。

### <a name="return-value"></a>傳回值

如果順利建立往來文章，非零值。否則為 0。

### <a name="remarks"></a>備註

使用`AfxBeginThread`建立執行緒物件，並在一個步驟中執行它。 使用`CreateThread`如果您想要重複使用後續的建立與終止執行緒執行的執行緒物件。

##  <a name="cwinthread"></a>  CWinThread::CWinThread

建構 `CWinThread` 物件。

```
CWinThread();
```

### <a name="remarks"></a>備註

若要開始執行緒的執行，請呼叫[CreateThread](#createthread)成員函式。 您通常會建立執行緒藉由呼叫[AfxBeginThread](application-information-and-management.md#afxbeginthread)，其會呼叫這個建構函式和`CreateThread`。

##  <a name="exitinstance"></a>  CWinThread::ExitInstance

由從架構中很少覆寫呼叫[執行](#run)成員函式來結束這個執行個體的執行緒，或如果呼叫[InitInstance](#initinstance)失敗。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>傳回值

執行緒的結束代碼;0 表示沒有錯誤，而大於 0 的值會指出錯誤。 此值可以藉由呼叫擷取[GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)。

### <a name="remarks"></a>備註

請勿呼叫此成員函式從任何地方但內`Run`成員函式。 此成員函式只能用於使用者介面執行緒。

此函式的預設實作會刪除`CWinThread`物件，如果[create_suspended](#m_bautodelete)為 TRUE。 如果您想要執行額外的清除，您的執行緒終止時，請覆寫這個函式。 實作`ExitInstance`執行您的程式碼之後，應該呼叫基底類別版本。

##  <a name="getmainwnd"></a>  CWinThread::GetMainWnd

如果您的應用程式是 OLE 伺服器，呼叫此函式可擷取應用程式，而不是直接參考的現用主視窗的指標`m_pMainWnd`應用程式物件的成員。

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>傳回值

此函式傳回下列其中一種 windows 的指標。 如果您的執行緒是 OLE 伺服器的一部分，而且已就地啟用作用中的容器內的物件，此函數會傳回[CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd)資料成員`CWinThread`物件。

如果不是就地啟用作用中的容器內的物件，或您的應用程式不是 OLE 伺服器，此函數會傳回[m_pMainWnd](#m_pmainwnd)執行緒物件資料成員。

### <a name="remarks"></a>備註

使用者介面執行緒，這相當於直接參考`m_pActiveWnd`應用程式物件的成員。

如果您的應用程式不是 OLE 伺服器，則呼叫此函式和直接參考應用程式物件的 `m_pMainWnd` 成員的功用相同。

覆寫這個函式來修改預設行為。

##  <a name="getthreadpriority"></a>  CWinThread::GetThreadPriority

取得這個執行緒的目前執行緒優先權層級。

```
int GetThreadPriority();
```

### <a name="return-value"></a>傳回值

其優先順序類別內目前的執行緒優先權等級。 傳回的值將會是其中一個下列命令，列出優先順序從高到最低：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

如需有關這些優先順序的詳細資訊，請參閱 < [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

##  <a name="initinstance"></a>  CWinThread::InitInstance

`InitInstance` 必須覆寫來初始化每個使用者介面執行緒的新執行個體。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>傳回值

如果初始化成功則為非零否則為 0。

### <a name="remarks"></a>備註

通常，您會覆寫`InitInstance`來執行工作，必須先完成，當第一次建立的執行緒。

此成員函式只能用於使用者介面執行緒。 傳遞至控制函式中執行的背景工作執行緒的初始設定[AfxBeginThread](application-information-and-management.md#afxbeginthread)。

##  <a name="isidlemessage"></a>  CWinThread::IsIdleMessage

覆寫此函式可保留`OnIdle`產生特定的訊息後呼叫。

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向目前正在處理的訊息。

### <a name="return-value"></a>傳回值

非零`OnIdle`處理之後，應該呼叫訊息; 否則為 0。

### <a name="remarks"></a>備註

預設實作不會呼叫`OnIdle`備援滑鼠訊息及產生的插入號閃爍一次訊息之後。

如果應用程式已建立簡短的計時器，`OnIdle`會呼叫經常造成效能問題。 若要改善這類應用程式的效能，覆寫`IsIdleMessage`應用程式的`CWinApp`-衍生類別，以檢查 WM_TIMER 訊息，如下所示：

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

以這種方式處理 WM_TIMER 會改善使用簡短的計時器的應用程式的效能。

##  <a name="m_bautodelete"></a>  CWinThread::m_bAutoDelete

指定在執行緒終止時是否要自動刪除 `CWinThread` 物件。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>備註

`m_bAutoDelete`資料成員是型別 BOOL 的公用變數。

`m_bAutoDelete` 的值不會影響基礎執行緒控制代碼如何關閉。 在 `CWinThread` 物件終結時，執行緒控制代碼永遠關閉。

##  <a name="m_hthread"></a>  CWinThread::m_hThread

附加至這個執行緒的控制代碼`CWinThread`。

```
HANDLE m_hThread;
```

### <a name="remarks"></a>備註

`m_hThread`資料成員是型別控制代碼的公用變數。 如果基礎執行緒目前存在，才有效。

##  <a name="m_nthreadid"></a>  CWinThread::m_nThreadID

執行緒識別碼附加至這個`CWinThread`。

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>備註

`m_nThreadID`資料成員是 DWORD 類型的公用變數。 如果基礎執行緒目前存在，才有效。

### <a name="example"></a>範例

  範例，請參閱[AfxGetThread](application-information-and-management.md#afxgetthread)。

##  <a name="m_pactivewnd"></a>  CWinThread::m_pActiveWnd

您可以使用此資料成員來儲存執行緒的作用中視窗物件的指標。

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>備註

Microsoft Foundation 類別庫會自動終止您的執行緒，當所參考的視窗`m_pActiveWnd`已關閉。 如果這個執行緒是主執行緒的應用程式，應用程式也會被終止。 如果此資料成員是 NULL，應用程式的使用中視窗`CWinApp`會繼承的物件。 `m_pActiveWnd` 這類型的公用變數`CWnd*`。

一般而言，您將此成員變數當您覆寫`InitInstance`。 在背景工作執行緒中，此資料成員的值被繼承自父執行緒。

##  <a name="m_pmainwnd"></a>  CWinThread::m_pMainWnd

您可以使用此資料成員來儲存執行緒的主視窗物件的指標。

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>備註

Microsoft Foundation 類別庫會自動終止您的執行緒，當所參考的視窗`m_pMainWnd`已關閉。 如果這個執行緒是主執行緒的應用程式，應用程式也會被終止。 如果此資料成員是 NULL，應用程式的主視窗`CWinApp`物件將用來判斷何時要終止執行緒。 `m_pMainWnd` 這類型的公用變數`CWnd*`。

一般而言，您將此成員變數當您覆寫`InitInstance`。 在背景工作執行緒中，此資料成員的值被繼承自父執行緒。

##  <a name="onidle"></a>  CWinThread::OnIdle

若要執行閒置時間處理此成員函式會覆寫。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>參數

*lCount*<br/>
每次遞增計數器`OnIdle`執行緒之訊息佇列是空的時呼叫。 這個計數會重設為 0 每次處理新訊息時。 您可以使用*lCount*參數，來判斷相對的執行緒已經閒置而不處理訊息的時間長度。

### <a name="return-value"></a>傳回值

非零值，以接收更多閒置處理時間;如果沒有更多閒置的處理時間需要，0。

### <a name="remarks"></a>備註

`OnIdle` 預設訊息迴圈中時呼叫的執行緒訊息佇列是空的。 使用覆寫來呼叫您自己的背景工作閒置處理常式。

`OnIdle` 應該會傳回 0，表示所需的任何其他的閒置處理時間。 *LCount*參數就會遞增每次`OnIdle`時的訊息佇列是空的會重設為 0 每次處理新訊息時呼叫。 您可以呼叫您不同的閒置常式，此計數為基礎。

此成員函式的預設實作會在暫存物件和未使用的動態連結程式庫，從記憶體釋放。

此成員函式只能用於使用者介面執行緒。

因為應用程式無法處理訊息，直到`OnIdle`傳回，這個函式中不執行冗長的工作。

##  <a name="operator_handle"></a>  CWinThread::operator 控制代碼

擷取的控制代碼`CWinThread`物件。

```
operator HANDLE() const;
```

### <a name="return-value"></a>傳回值

如果成功，執行緒物件的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

直接呼叫 Windows Api 中使用的控制代碼。

##  <a name="postthreadmessage"></a>  CWinThread::PostThreadMessage

若要將使用者定義訊息張貼至另一個呼叫`CWinThread`物件。

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*message*<br/>
使用者定義訊息的識別碼。

*wParam*<br/>
第一個訊息參數。

*lParam*<br/>
第二個訊息參數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

已發佈的訊息是由訊息對應巨集 ON_THREAD_MESSAGE 對應至適當的訊息處理常式。

> [!NOTE]
> 當您呼叫[PostThreadMessage](/windows/desktop/api/winuser/nf-winuser-postthreadmessagea)，訊息會放在執行緒之訊息佇列。 不過，因為張貼這種方式的訊息不是與視窗相關聯的 MFC 就不發送到訊息或命令處理常式。 為了處理這些訊息，覆寫`PreTranslateMessage()`函式的程式 CWinApp 衍生類別，並以手動方式處理的訊息。

##  <a name="pretranslatemessage"></a>  CWinThread::PreTranslateMessage

覆寫這個函式來篩選視窗訊息，再將它們分派至 Windows 函式[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指向[MSG 結構](../../mfc/reference/msg-structure1.md)包含要處理的訊息。

### <a name="return-value"></a>傳回值

如果訊息已完全處理中為非零`PreTranslateMessage`，不應進一步處理。 如果應該以一般方式處理訊息，則為零。

### <a name="remarks"></a>備註

此成員函式只能用於使用者介面執行緒。

##  <a name="processmessagefilter"></a>  CWinThread::ProcessMessageFilter

架構的攔截函式會呼叫此成員函式，來篩選及回應特定 Windows 訊息。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*程式碼*<br/>
指定攔截程式碼。 此成員函式會使用程式碼來判斷如何處理*lpMsg。*

*lpMsg*<br/>
Windows 的指標[MSG 結構](../../mfc/reference/msg-structure1.md)。

### <a name="return-value"></a>傳回值

如果訊息已處理，非零值。否則為 0。

### <a name="remarks"></a>備註

攔截函式會處理傳送至應用程式的一般訊息之前的事件處理。

如果您覆寫此進階的功能，請務必呼叫基底類別版本，以維護的架構連接處理。

##  <a name="processwndprocexception"></a>  CWinThread::ProcessWndProcException

每當處理常式不會攔截在一個執行緒的訊息或命令處理常式中擲回例外狀況時，架構會呼叫此成員函式。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>參數

*e*<br/>
若要處理的例外狀況的點。

*pMsg*<br/>
指向[MSG 結構](../../mfc/reference/msg-structure1.md)包含導致擲回例外狀況架構的 windows 訊息的相關資訊。

### <a name="return-value"></a>傳回值

如果產生 WM_CREATE 例外狀況;-1否則為 0。

### <a name="remarks"></a>備註

請勿直接呼叫此成員函式。

此成員函式的預設實作會處理只能從下列訊息所產生的例外狀況：

|命令|動作|
|-------------|------------|
|WM_CREATE|失敗。|
|WM_PAINT|驗證受影響的視窗中，以防止另一個 WM_PAINT 訊息所產生。|

覆寫此成員函式，來提供全域處理您的例外狀況。 只有當您想要顯示的預設行為，請呼叫基底功能。

此成員函式只能用於有訊息幫浦的執行緒。

##  <a name="pumpmessage"></a>  CWinThread::PumpMessage

包含執行緒的訊息迴圈。

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>備註

`PumpMessage` 包含執行緒的訊息迴圈。 `PumpMessage` 會呼叫`CWinThread`到幫浦執行緒的訊息。 您可以呼叫`PumpMessage`直接強制訊息處理，或者您可以覆寫`PumpMessage`變更其預設行為。

呼叫`PumpMessage`直接覆寫其預設行為僅適用於進階使用者建議。

##  <a name="resumethread"></a>  Cwinthread:: Resumethread

若要繼續執行已暫止的執行緒呼叫[SuspendThread](#suspendthread)成員函式或建立 CREATE_SUSPENDED 旗標的執行緒。

```
DWORD ResumeThread();
```

### <a name="return-value"></a>傳回值

先前在執行緒的暫停計數，如果登錄成功。`0xFFFFFFFF`否則。 傳回值為零，如果目前執行緒已不會暫停。 如果傳回的值為 1，執行緒就會暫止，但現在重新啟動。 任何大於一表示執行緒的傳回值會保持暫停。

### <a name="remarks"></a>備註

目前執行緒的暫停計數會減 1。 如果暫停計數會減為零，執行緒會繼續執行;否則，執行緒會保持暫停。

##  <a name="run"></a>  Cwinthread:: Run

提供使用者介面執行緒中的預設訊息迴圈。

```
virtual int Run();
```

### <a name="return-value"></a>傳回值

**Int**執行緒所傳回的值。 此值可以藉由呼叫擷取[GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)。

### <a name="remarks"></a>備註

`Run` 取得，然後將 Windows 訊息的分派，直到應用程式接收[WM_QUIT](/windows/desktop/winmsg/wm-quit)訊息。 如果目前執行緒之訊息佇列不包含的任何訊息，`Run`呼叫`OnIdle`執行閒置時間處理。 內送訊息會移至[PreTranslateMessage](#pretranslatemessage)成員函式進行特殊處理，然後 Windows 函式[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)標準鍵盤轉譯。 最後， [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)呼叫 Windows 函式。

`Run` 很少會覆寫，但您可以覆寫該實作特殊的行為。

此成員函式只能用於使用者介面執行緒。

##  <a name="setthreadpriority"></a>  CWinThread::SetThreadPriority

此函式會設定其優先權類別內目前的執行緒的優先權層級。

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>參數

*nPriority*<br/>
指定新的執行緒優先權等級，其優先順序類別內。 這個參數必須是下列值，列出優先順序從高到最低的其中一個：

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

如需有關這些優先順序的詳細資訊，請參閱 < [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

### <a name="return-value"></a>傳回值

非零值，如果函式執行成功;否則為 0。

### <a name="remarks"></a>備註

它只能呼叫之後[CreateThread](#createthread)成功傳回。

##  <a name="suspendthread"></a>  CWinThread::SuspendThread

遞增目前執行緒的暫停計數。

```
DWORD SuspendThread();
```

### <a name="return-value"></a>傳回值

先前在執行緒的暫停計數，如果登錄成功。`0xFFFFFFFF`否則。

### <a name="remarks"></a>備註

如果任何執行緒的暫停計數高於零，則不會執行該執行緒。 執行緒可以藉由呼叫繼續[ResumeThread](#resumethread)成員函式。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
