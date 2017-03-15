---
title: "CWinThread 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinThread
dev_langs:
- C++
helpviewer_keywords:
- worker threads
- threading [MFC], safety
- CWinThread class
- threading [MFC], creating threads
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 866e847f9c1d73d6f9882e50b1274fbad9e21a39
ms.lasthandoff: 02/24/2017

---
# <a name="cwinthread-class"></a>CWinThread 類別
代表應用程式內執行的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinThread::CWinThread](#cwinthread)|建構 `CWinThread` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinThread::CreateThread](#createthread)|開始執行`CWinThread`物件。|  
|[CWinThread::ExitInstance](#exitinstance)|覆寫您的執行緒終止時清除。|  
|[CWinThread::GetMainWnd](#getmainwnd)|擷取執行緒的主視窗的指標。|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|取得目前執行緒的優先權。|  
|[CWinThread::InitInstance](#initinstance)|覆寫以執行執行緒的執行個體初始化。|  
|[CWinThread::IsIdleMessage](#isidlemessage)|檢查有無特殊訊息。|  
|[CWinThread::OnIdle](#onidle)|覆寫以執行執行緒特定的閒置時間處理。|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|將訊息張貼到另一個`CWinThread`物件。|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|篩選訊息，再分派這些 Windows 函式[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|到達應用程式之前，會攔截某些訊息。|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|攔截所有執行緒的訊息和命令處理常式擲回的未處理例外狀況。|  
|[CWinThread::PumpMessage](#pumpmessage)|包含執行緒的訊息迴圈。|  
|[CWinThread::ResumeThread](#resumethread)|減少執行緒的暫停計數。|  
|[Cwinthread:: Run](#run)|使用訊息幫浦的控制執行緒的函式。 若要自訂預設的訊息迴圈會覆寫。|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|設定目前執行緒的優先權。|  
|[CWinThread::SuspendThread](#suspendthread)|增加執行緒的暫停計數。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinThread::operator 控制代碼](#operator_handle)|擷取的控制代碼`CWinThread`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|指定是否要終結物件在執行緒終止。|  
|[CWinThread::m_hThread](#m_hthread)|目前執行緒的控制代碼。|  
|[CWinThread::m_nThreadID](#m_nthreadid)|目前執行緒的識別碼。|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|容器應用程式是 OLE 伺服器時就地啟用作用中的主視窗的指標。|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|保留應用程式的主視窗的指標。|  
  
## <a name="remarks"></a>備註  
 執行主執行緒通常會提供物件衍生自`CWinApp`;`CWinApp`衍生自`CWinThread`。 其他`CWinThread`物件允許在指定的應用程式中的多個執行緒。  
  
 有兩種一般的執行緒，`CWinThread`支援︰ 背景工作執行緒和使用者介面執行緒。 背景工作執行緒有任何訊息幫浦︰ 例如，在試算表應用程式中執行背景計算的執行緒。 使用者介面執行緒擁有訊息幫浦，並處理從系統收到的訊息。 [CWinApp](../../mfc/reference/cwinapp-class.md)和從它衍生的類別是使用者介面執行緒的範例。 其他使用者介面執行緒也可以直接從衍生`CWinThread`。  
  
 類別的物件`CWinThread`通常存在期間的執行緒。 如果您想要修改此行為，設定[m_bAutoDelete](#m_bautodelete)至**FALSE**。  
  
 `CWinThread`類別是為了讓您的程式碼及 MFC 完整安全執行緒。 執行緒區域資料架構用來維護執行緒特定的資訊由`CWinThread`物件。 由於此依賴`CWinThread`處理執行緒區域資料，任何使用 MFC 的執行緒必須由 MFC。 例如，執行階段函式所建立的執行緒[_beginthread、 _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)不能使用任何 MFC Api。  
  
 若要建立的執行緒，呼叫[AfxBeginThread](application-information-and-management.md#afxbeginthread)。 有兩種形式，取決於您的背景工作角色或使用者介面執行緒。 如果您要使用者介面執行緒，傳遞給`AfxBeginThread`指標`CRuntimeClass`的您`CWinThread`-衍生的類別。 如果您想要建立一個背景工作執行緒，傳遞給`AfxBeginThread`控制函式並使用參數來控制函式的指標。 背景工作執行緒和使用者介面執行緒中，您可以指定修改優先順序、 堆疊大小、 建立旗標，以及安全性屬性的選擇性參數。 `AfxBeginThread`將指標傳回給您的新`CWinThread`物件。  
  
 而不是呼叫`AfxBeginThread`，您可以建構`CWinThread`-衍生物件，然後再呼叫`CreateThread`。 如果您想要重複使用這個兩階段建構方法相當實用`CWinThread`連續建立與終止執行緒執行的物件。  
  
 如需有關`CWinThread`，請參閱文章[多執行緒 c + + 和 MFC](../../parallel/multithreading-with-cpp-and-mfc.md)，[多執行緒︰ 建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)，[多執行緒︰ 建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)，和[多執行緒︰ 如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecreatethreada--cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::CreateThread  
 建立執行緒來呼叫程序的位址空間內執行。  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwCreateFlags`  
 指定另一個旗標會控制執行緒的建立。 這個旗標可以包含兩個值之一︰  
  
- **CREATE_SUSPENDED**啟動與暫停計數的其中一個執行緒。 使用**CREATE_SUSPENDED**如果您想要初始化的任何成員資料`CWinThread`物件，例如[m_bAutoDelete](#m_bautodelete)或衍生類別中，執行緒開始執行之前的任何成員。 當您初始化完成之後，使用[CWinThread::ResumeThread](#resumethread)開始執行的執行緒。 執行緒不會執行直到`CWinThread::ResumeThread`呼叫。  
  
- **0**建立後立即啟動執行緒。  
  
 `nStackSize`  
 指定的大小，以位元組為單位的新執行緒的堆疊。 如果**0**，堆疊大小預設為相同大小的處理序的主要執行緒。  
  
 `lpSecurityAttrs`  
 指向[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定執行緒的安全性屬性。  
  
### <a name="return-value"></a>傳回值  
 非零，如果執行緒建立可順利啟動。否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`AfxBeginThread`建立執行緒物件，並執行一次。 使用`CreateThread`如果您想要重複使用連續建立與終止執行緒執行的執行緒物件。  
  
##  <a name="a-namecwinthreada--cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread  
 建構 `CWinThread` 物件。  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>備註  
 若要開始執行的執行緒，請呼叫[CreateThread](#createthread)成員函式。 您通常會建立執行緒藉由呼叫[AfxBeginThread](http://msdn.microsoft.com/library/e9e8684d-24f7-4599-8fdf-1f4f560a753b)，它會呼叫這個建構函式和`CreateThread`。  
  
##  <a name="a-nameexitinstancea--cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::ExitInstance  
 從架構，很少覆寫呼叫[執行](#run)成員函式來結束此執行個體的執行緒，或如果呼叫[InitInstance](#initinstance)失敗。  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>傳回值  
 在執行緒結束代碼。0 表示沒有錯誤，以及大於 0 的值表示錯誤。 這個值可以藉由呼叫擷取[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)。  
  
### <a name="remarks"></a>備註  
 請勿呼叫此成員函式從任何地方但內**執行**成員函式。 此成員函式只能用於使用者介面執行緒。  
  
 此函式的預設實作會刪除`CWinThread`物件如果[m_bAutoDelete](#m_bautodelete)是**TRUE**。 如果您想要執行其他清除工作，您的執行緒終止時，請覆寫這個函式。 實作`ExitInstance`執行您的程式碼之後，應該呼叫基底類別版本。  
  
##  <a name="a-namegetmainwnda--cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd  
 如果您的應用程式是 OLE 伺服器，呼叫此函式可擷取而不是直接參考應用程式的使用中的主視窗的指標`m_pMainWnd`應用程式物件的成員。  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>傳回值  
 此函式傳回下列其中一種 windows 的指標。 如果您的執行緒屬於 OLE 伺服器，而且已在使用中的容器內就地啟動的物件，此函數會傳回[CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd)資料成員的`CWinThread`物件。  
  
 如果沒有物件的容器內就地啟動或應用程式並非 OLE 伺服器，此函數會傳回[m_pMainWnd](#m_pmainwnd)執行緒物件資料成員。  
  
### <a name="remarks"></a>備註  
 對於使用者介面執行緒，這是相當直接參考`m_pActiveWnd`應用程式物件的成員。  
  
 如果您的應用程式不是 OLE 伺服器，則呼叫此函式和直接參考應用程式物件的 `m_pMainWnd` 成員的功用相同。  
  
 覆寫這個函式來修改預設行為。  
  
##  <a name="a-namegetthreadprioritya--cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority  
 取得這個執行緒目前的執行緒優先權等級。  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>傳回值  
 在其優先順序類別中目前的執行緒優先權等級。 傳回的值會是下列其中一個列出優先順序從高到最低︰  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 如需有關這些優先順序的詳細資訊，請參閱[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinitinstancea--cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance  
 `InitInstance`必須覆寫來初始化每個使用者介面執行緒的新執行個體。  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 通常，您會覆寫`InitInstance`執行時先建立一個執行緒都必須完成的工作。  
  
 此成員函式只能用於使用者介面執行緒。 在控制傳遞至函式中執行的背景工作執行緒的初始化[AfxBeginThread](application-information-and-management.md#afxbeginthread)。  
  
##  <a name="a-nameisidlemessagea--cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsIdleMessage  
 覆寫此函式可讓**OnIdle**後會產生特定的訊息時呼叫。  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 `pMsg`  
 指向目前正在處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果為非零`OnIdle`應該呼叫之後處理訊息; 否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作不會呼叫**OnIdle**備援滑鼠訊息後產生的插入號閃爍的訊息。  
  
 如果應用程式已建立簡短的計時器， **OnIdle**會呼叫次數頻繁，造成效能問題。 若要改善這類應用程式的效能，覆寫`IsIdleMessage`在應用程式的`CWinApp`-衍生的類別來檢查`WM_TIMER`訊息，如下所示︰  
  
 [!code-cpp[NVC_MFCDocView #&189;](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 處理`WM_TIMER`以這種方式將可改善效能的應用程式，使用簡短的計時器。  
  
##  <a name="a-namembautodeletea--cwinthreadmbautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete  
 指定在執行緒終止時是否要自動刪除 `CWinThread` 物件。  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>備註  
 `m_bAutoDelete`資料成員是類型的公用變數**BOOL**。  
  
 `m_bAutoDelete` 的值不會影響基礎執行緒控制代碼如何關閉。 在 `CWinThread` 物件終結時，執行緒控制代碼永遠關閉。  
  
##  <a name="a-namemhthreada--cwinthreadmhthread"></a><a name="m_hthread"></a>CWinThread::m_hThread  
 附加至這個執行緒的控制代碼`CWinThread`。  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>備註  
 `m_hThread`資料成員是類型的公用變數`HANDLE`。 如果目前的基礎執行緒存在，才有效。  
  
##  <a name="a-namemnthreadida--cwinthreadmnthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID  
 執行緒識別碼附加至這個`CWinThread`。  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>備註  
 **M_nThreadID**資料成員是類型的公用變數`DWORD`。 如果目前的基礎執行緒存在，才有效。  
  
### <a name="example"></a>範例  
  請參閱範例[AfxGetThread](application-information-and-management.md#afxgetthread)。  
  
##  <a name="a-namempactivewnda--cwinthreadmpactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd  
 使用此資料成員來儲存您的執行緒使用中視窗物件的指標。  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>備註  
 Mfc 程式庫會自動終止您的執行緒 視窗中所參考的`m_pActiveWnd`已關閉。 如果這個執行緒在主執行緒的應用程式，將會終止應用程式。 如果此資料成員是**NULL**，針對應用程式的使用中視窗`CWinApp`物件會被繼承。 `m_pActiveWnd`類型的公用變數**CWnd\***。  
  
 一般而言，您將此成員變數覆寫時`InitInstance`。 背景工作執行緒，此資料成員的值被繼承自父執行緒。  
  
##  <a name="a-namempmainwnda--cwinthreadmpmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd  
 使用此資料成員來儲存您的執行緒主視窗物件的指標。  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>備註  
 Mfc 程式庫會自動終止您的執行緒 視窗中所參考的`m_pMainWnd`已關閉。 如果這個執行緒在主執行緒的應用程式，將會終止應用程式。 如果此資料成員是**NULL**，應用程式的主視窗`CWinApp`物件將會用來決定何時終止執行緒。 `m_pMainWnd`類型的公用變數**CWnd\***。  
  
 一般而言，您將此成員變數覆寫時`InitInstance`。 背景工作執行緒，此資料成員的值被繼承自父執行緒。  
  
##  <a name="a-nameonidlea--cwinthreadonidle"></a><a name="onidle"></a>CWinThread::OnIdle  
 覆寫此成員函式，以執行閒置時間處理。  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>參數  
 `lCount`  
 每次遞增計數器`OnIdle`執行緒之訊息佇列為空白時，呼叫。 這個計數會重設為 0 每次處理新訊息時。 您可以使用`lCount`參數，來判斷相對的執行緒已經閒置而不處理訊息的時間長度。  
  
### <a name="return-value"></a>傳回值  
 非零值，以接收多閒置處理的時間;如果沒有更多閒置處理時間需要，0。  
  
### <a name="remarks"></a>備註  
 `OnIdle`預設訊息迴圈中時呼叫的執行緒訊息佇列是空的。 您可以使用覆寫來呼叫您自己的背景閒置處理常式的工作。  
  
 `OnIdle`應該會傳回 0，表示，不需要任何額外的閒置處理時間。 `lCount`參數會在每次遞增`OnIdle`時的訊息佇列是空的會重設為 0 每次處理新訊息時呼叫。 您可以呼叫您不同的閒置常式，此計數為基礎。  
  
 此成員函式的預設實作會在暫存物件和未使用的動態連結程式庫，從記憶體釋放。  
  
 此成員函式只能用於使用者介面執行緒。  
  
 因為應用程式無法處理訊息，直到`OnIdle`傳回，請勿執行此函式中的漫長的工作。  
  
##  <a name="a-nameoperatorhandlea--cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::operator 控制代碼  
 擷取的控制代碼`CWinThread`物件。  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，物件的控制代碼的執行緒。否則， **NULL**。  
  
### <a name="remarks"></a>備註  
 若要直接呼叫 Windows Api 中使用的控制代碼。  
  
##  <a name="a-namepostthreadmessagea--cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage  
 呼叫張貼到另一個使用者定義訊息`CWinThread`物件。  
  
```  
BOOL PostThreadMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `message`  
 使用者定義訊息的識別碼。  
  
 `wParam`  
 第一個訊息參數。  
  
 `lParam`  
 第二個訊息參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 已張貼的訊息由訊息對應巨集對應到適當的訊息處理常式`ON_THREAD_MESSAGE`。  
  
> [!NOTE]
>  當呼叫 Windows [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946)在 MFC 應用程式，MFC 訊息處理常式不會呼叫的函式。 如需詳細資訊，請參閱知識庫文件 」 PRB:: MFC 訊息處理常式不呼叫與 PostThreadMessage() 」 (Q142415)。  
  
##  <a name="a-namepretranslatemessagea--cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage  
 覆寫這個函式來篩選視窗訊息，再分派這些 Windows 函式[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)。  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 `pMsg`  
 指向[MSG 結構](../../mfc/reference/msg-structure1.md)包含要處理的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果在完全處理訊息為非零`PreTranslateMessage`，不應進一步處理。 如果應該以一般方式處理訊息，則為零。  
  
### <a name="remarks"></a>備註  
 此成員函式只能用於使用者介面執行緒。  
  
##  <a name="a-nameprocessmessagefiltera--cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter  
 架構的攔截函式會呼叫此成員函式，來篩選及回應特定 Windows 訊息。  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>參數  
 `code`  
 指定攔截程式碼。 此成員函式來判斷如何處理使用的程式碼`lpMsg.`  
  
 `lpMsg`  
 Windows 的指標[MSG 結構](../../mfc/reference/msg-structure1.md)。  
  
### <a name="return-value"></a>傳回值  
 如果已處理訊息為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 攔截函式會處理它們傳送到應用程式的一般訊息之前的事件處理。  
  
 如果您覆寫這項進階的功能，請務必呼叫基底類別版本來維護架構的攔截 (hook) 處理。  
  
##  <a name="a-nameprocesswndprocexceptiona--cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException  
 每當處理常式不會攔截在一個執行緒的訊息或命令處理常式中擲回例外狀況時，架構會呼叫此成員函式。  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 *e*  
 若要處理的例外狀況的點。  
  
 `pMsg`  
 指向[MSG 結構](../../mfc/reference/msg-structure1.md)包含導致擲回例外狀況架構的 windows 訊息的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 – 1，否則`WM_CREATE`會產生例外狀況; 否則為 0。  
  
### <a name="remarks"></a>備註  
 請勿直接呼叫此成員函式。  
  
 此成員函式的預設實作會處理從下列訊息產生的例外︰  
  
|命令|動作|  
|-------------|------------|  
|`WM_CREATE`|失敗。|  
|`WM_PAINT`|驗證受影響的視窗中，因而導致另一個`WM_PAINT`而產生的訊息。|  
  
 若要提供您的例外狀況的通用處理此成員函式會覆寫。 只有當您想要顯示的預設行為，請呼叫的基本功能。  
  
 此成員函式只能用於有訊息幫浦的執行緒。  
  
##  <a name="a-namepumpmessagea--cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage  
 包含執行緒的訊息迴圈。  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>備註  
 `PumpMessage`包含執行緒的訊息迴圈。 **PumpMessage**由呼叫`CWinThread`到執行緒的訊息幫浦 」。 您可以呼叫`PumpMessage`直接強制訊息處理，或者您可以覆寫`PumpMessage`變更其預設行為。  
  
 呼叫`PumpMessage`直接覆寫其預設行為僅供進階使用者建議。  
  
##  <a name="a-nameresumethreada--cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread::ResumeThread  
 若要繼續執行暫停的執行緒呼叫[SuspendThread](#suspendthread)成員函式或建立的執行緒**CREATE_SUSPENDED**旗標。  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>傳回值  
 執行緒的上一個暫停計數，如果登錄成功。`0xFFFFFFFF`否則。 傳回值為零，如果已不會暫停目前的執行緒。 傳回值為&1;，如果執行緒暫止，但是現在重新啟動。 任何傳回的值大於一表示執行緒保持暫停。  
  
### <a name="remarks"></a>備註  
 目前執行緒的暫停次數會減少一個。 如果暫停計數會減為零，執行緒會繼續執行。否則，執行緒會保持暫停。  
  
##  <a name="a-nameruna--cwinthreadrun"></a><a name="run"></a>Cwinthread:: Run  
 提供使用者介面執行緒的預設訊息迴圈。  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>傳回值  
 `int`執行緒所傳回的值。 這個值可以藉由呼叫擷取[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)。  
  
### <a name="remarks"></a>備註  
 **執行**取得，而且會分派 Windows 訊息，直到應用程式收到[WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641)訊息。 如果目前執行緒之訊息佇列不包含的任何訊息，**執行**呼叫`OnIdle`執行閒置時間處理。 內送訊息會移至[PreTranslateMessage](#pretranslatemessage)成員函式進行特殊處理，然後以 Windows 函式[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)標準鍵盤翻譯。 最後， [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)呼叫 Windows 函式。  
  
 **執行**幾乎不覆寫，但您可以覆寫它實作特殊行為。  
  
 此成員函式只能用於使用者介面執行緒。  
  
##  <a name="a-namesetthreadprioritya--cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority  
 此函式會將其優先順序類別目前執行緒的優先權層級。  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>參數  
 `nPriority`  
 指定新的執行緒優先權層級在其優先順序類別中。 這個參數必須是下列值，列出優先順序從高到最低的其中一個︰  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 如需有關這些優先順序的詳細資訊，請參閱[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 它之後，才會呼叫[CreateThread](#createthread)成功傳回。  
  
##  <a name="a-namesuspendthreada--cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread::SuspendThread  
 遞增目前執行緒的暫停計數。  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>傳回值  
 執行緒的上一個暫停計數，如果登錄成功。`0xFFFFFFFF`否則。  
  
### <a name="remarks"></a>備註  
 如果任何執行緒的暫停計數高於零，則不會執行該執行緒。 執行緒可以繼續藉由呼叫[ResumeThread](#resumethread)成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)

