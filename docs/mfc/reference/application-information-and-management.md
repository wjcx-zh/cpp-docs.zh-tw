---
title: "應用程式資訊和管理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: b943ef8dd652df061965fe81ecc9c08115636141
ms.openlocfilehash: 5d7b6a0c31a8c4ff63b3cfc1fa58c08879e37f58
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="application-information-and-management"></a>應用程式資訊和管理
當您撰寫應用程式時，您會建立單一[CWinApp](../../mfc/reference/cwinapp-class.md)-衍生物件。 有時候，您可能想要取得此物件從外部的相關資訊`CWinApp`-衍生物件。 或者，您可能需要其他全域"mananger 」 物件的存取權。
  
 Microsoft Foundation 類別庫提供下列全域函式，可協助您完成這些工作︰  
  
### <a name="application-information-and-management-functions"></a>應用程式資訊和管理功能  
  
|||  
|-|-|  
|[AfxBeginThread](#afxbeginthread)|建立新的執行緒。|  
|[AfxContextMenuManager](#afxcontextmenumanager)|指標的全域[內容功能表管理員](ccontextmenumanager-class.md)。|
|[AfxEndThread](#afxendthread)|會結束目前的執行緒。|  
|[AfxFindResourceHandle](#afxfindresourcehandle)|將逐步引導資源鏈結並找出特定資源的資源識別碼與資源類型。 |
|[AfxFreeLibrary](#afxfreelibrary)|遞減參考計數的載入的動態連結程式庫 (DLL) 模組。當參考計數到達零時，模組未產生對應。|  
|[AfxGetApp](#afxgetapp)|傳回指向應用程式的單一`CWinApp`物件。|  
|[AfxGetAppName](#afxgetappname)|傳回字串，包含應用程式的名稱。|  
|[AfxGetInstanceHandle](#afxgetinstancehandle)|傳回`HINSTANCE`代表應用程式的這個執行個體。|  
|[AfxGetMainWnd](#afxgetmainwnd)|讓指標回到目前"main"視窗的非 OLE 應用程式或伺服器應用程式的就地框架視窗。|  
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函數來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** ( **HKCU**) 節點。|  
|[AfxGetResourceHandle](#afxgetresourcehandle)|傳回`HINSTANCE`的應用程式的預設資源的來源。 使用這個來直接存取應用程式的資源。|  
|[AfxGetThread](#afxgetthread)|擷取目前的指標[CWinThread](../../mfc/reference/cwinthread-class.md)物件。|  
|[AfxInitRichEdit](#afxinitrichedit)|初始化 1.0 的 rich edit 控制項的應用程式的版本。|  
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化 2.0 和更新版本的 rich edit 控制項的應用程式的版本。| 
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|判斷指定的視窗是否為擴充框架物件。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|判斷指定的視窗是否為工具列物件。|
|[AfxKeyboardManager](#afxkeyboardmanager)|指標的全域[鍵盤管理員](ckeyboardmanager-class.md)。|
|[AfxLoadLibrary](#afxloadlibrary)|對應 DLL 模組，並傳回的控制代碼，可用來取得 DLL 函式的位址。|  
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|指標的全域[可功能表管理員](cmenutearoffmanager-class.md)。|
|[AfxMouseManager](#afxmousemanager)|指標的全域[滑鼠管理員](cmousemanager-class.md)。|
|[AfxRegisterClass](#afxregisterclass)|註冊視窗類別中使用 MFC 的 DLL。|  
|[AfxRegisterWndClass](#afxregisterwndclass)|註冊以補充那些由 MFC 自動註冊的 Windows 視窗類別。|  
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|設定應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|  
|[AfxSetResourceHandle](#afxsetresourcehandle)|設定`HINSTANCE`控制代碼的應用程式的預設資源的載入位置。|  
|[AfxShellManager](#afxshellmanager)|指標的全域[殼層管理員](cshellmanager-class.md)。 |
|[AfxSocketInit](#afxsocketinit)|在呼叫`CWinApp::InitInstance`初始化 Windows Sockets 的覆寫。|  
|[AfxUserToolsManager](#afxusertoolsmanager)|指標的全域[使用者工具管理員](cusertoolsmanager-class.md)。|
|[AfxWinInit](#afxwininit)|由 MFC 提供呼叫`WinMain`函式，做為一部分[CWinApp](../../mfc/reference/cwinapp-class.md)的 GUI 型的應用程式，以初始化 MFC 初始化。 必須針對使用 MFC 的主控台應用程式直接呼叫。|  
  

  
##  <a name="afxbeginthread"></a>AfxBeginThread  
 呼叫此函式可建立新的執行緒。  
  
```   
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,  
    LPVOID pParam,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL); 
```  
  
### <a name="parameters"></a>參數  
 `pfnThreadProc`  
 指向以背景工作執行緒控制函式。 不能**NULL**。 此函式必須宣告，如下所示︰  
  
 `UINT __cdecl MyControllingFunction( LPVOID pParam );`  
  
 *pThreadClass*  
 物件的 RUNTIME_CLASS 衍生自[CWinThread](../../mfc/reference/cwinthread-class.md)。  
  
 *pParam*  
 參數要傳遞給控制函式中的函式宣告的參數中所示`pfnThreadProc`。  
  
 `nPriority`  
 所需的執行緒的優先權。 如需完整清單和描述可用的優先順序，請參閱[SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) Windows SDK 中。  
  
 `nStackSize`  
 指定的大小，以位元組為單位的新執行緒的堆疊。 如果為 0，堆疊大小預設堆疊大小相同與建立的執行緒。  
  
 `dwCreateFlags`  
 指定控制的執行緒建立的額外旗標。 這個旗標可以包含兩個值之一︰  
  
- **CREATE_SUSPENDED**暫停計數為其中一個啟動執行緒。 使用**CREATE_SUSPENDED**如果您想要初始化的任何成員資料`CWinThread`物件，例如[m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete)或衍生類別中，執行緒開始執行之前的任何成員。 當您初始化完成之後，使用[CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread)開始執行的執行緒。 執行緒不會執行直到`CWinThread::ResumeThread`呼叫。  
  
- **0**在建立後立即啟動執行緒。  
  
 `lpSecurityAttrs`  
 指向[ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定在執行緒的安全性屬性。 如果**NULL**，相同的安全性屬性，因為會使用建立的執行緒。 如需有關此結構的詳細資訊，請參閱 Windows SDK。  
  
### <a name="return-value"></a>傳回值  
 新建立的執行緒物件、 指標或**NULL**如果發生失敗。  
  
### <a name="remarks"></a>備註  
 第一種形式的`AfxBeginThread`建立背景工作執行緒。 第二種形式建立的執行緒，可能會做為使用者介面執行緒或背景工作執行緒。  
  
 `AfxBeginThread`建立新`CWinThread`物件，會呼叫其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函式來開始執行的執行緒，並傳回執行緒的指標。 整個程序進行檢查以確定所有物件都都會解除配置建立的任何部分失敗。 若要結束的執行緒，請呼叫[AfxEndThread](#afxendthread)從內的執行緒或從背景工作執行緒的控制函式傳回。  
  
 必須啟用多執行緒應用程式。否則，此函式將會失敗。 如需啟用多執行緒處理的詳細資訊，請參閱[/MD、 /MT、 /LD （使用執行階段程式庫）](../../build/reference/md-mt-ld-use-run-time-library.md)下*Visual c + + 編譯器選項*。  
  
 如需有關`AfxBeginThread`，請參閱文章[多執行緒︰ 建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)和[多執行緒︰ 建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)。  
  
### <a name="example"></a>範例  
 請參閱範例的[CSocket::Attach](../../mfc/reference/csocket-class.md#attach)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  

## <a name="afxcontextmenumanager"></a>AfxContextMenuManager
指標的全域[內容功能表管理員](ccontextmenumanager-class.md)。  
   
### <a name="syntax"></a>語法    
```  
CContextMenuManager* afxContextMenuManager;  
```     
### <a name="requirements"></a>需求  
 **標頭︰** afxcontextmenumanager.h     

### <a name="see-also"></a>另請參閱   
 [CContextMenuManager 類別](ccontextmenumanager-class.md)

  
##  <a name="afxendthread"></a>AfxEndThread  
 呼叫此函式來結束目前執行中執行緒。  
  
```   
void AFXAPI AfxEndThread(
    UINT nExitCode,  
    BOOL bDelete  = TRUE); 
```  
  
### <a name="parameters"></a>參數  
 *nExitCode*  
 指定執行緒的結束代碼。  
  
 *bDelete*  
 從記憶體刪除執行緒物件。  
  
### <a name="remarks"></a>備註  
 必須從呼叫終止執行緒內。  
  
 如需有關`AfxEndThread`，請參閱文章[多執行緒︰ 結束執行緒](../../parallel/multithreading-terminating-threads.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
使用 `AfxFindResourceHandle` 查核資源鏈結並依資源 ID 和資源類型尋找特定的資源。  
   
### <a name="syntax"></a>語法    
```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );  
```
### <a name="parameters"></a>參數  
 `lpszName`  
 包含資源 ID 之字串的指標。    
 *lpszType*  
 資源類型的指標。 如需資源類型的清單，請參閱[FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) Windows SDK 中。  
   
### <a name="return-value"></a>傳回值  
 包含資源之模組的控制代碼。  
   
### <a name="remarks"></a>備註  
 `AfxFindResourceHandle` 會尋找特定資源並將控制代碼傳回到包含資源的模組。 資源可能會位於您載入的任一個擴充 DLL 中。 `AfxFindResourceHandle` 會告知您哪一個 DLL 中內含資源。  
  
 模組會依此順序搜尋：  
  
1.  主要模組 (如果它是一個擴充 DLL)。  
  
2.  非系統模組。  
  
3.  特定語言的模組。  
  
4.  主要模組 (如果它是系統 DLL)。  
  
5.  系統模組。  
   
### <a name="requirements"></a>需求  
 **標題:** afxwin.h  
   
### <a name="see-also"></a>另請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
  
##  <a name="afxfreelibrary"></a>AfxFreeLibrary  
 `AfxFreeLibrary` 和 `AfxLoadLibrary` 會保留每個載入的程式庫模組的參考計數。  
  
```   
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib); 
```  
  
### <a name="parameters"></a>參數  
 *hInstLib*  
 所載入程式庫模組的控制代碼。 [AfxLoadLibrary](#afxloadlibrary)傳回這個控制代碼。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**函式成功; 如果否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 `AfxFreeLibrary` 會將載入的動態連結程式庫 (DLL) 模組的參考計數遞減。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。 每次呼叫 `AfxLoadLibrary` 時，此參考計數會遞增。  
  
 在取消對應程式庫模組之前，系統會啟用 DLL 來中斷處理序使用它的連結。 這樣做可讓 DLL 代表目前的處理序清除已配置的資源。 在進入點函式傳回之後，程式庫模組就會從目前處理序的位址空間中移除。  
  
 使用 `AfxLoadLibrary` 對應 DLL 模組。  
  
 務必使用`AfxFreeLibrary`和`AfxLoadLibrary`(而不是 Win32 函式**FreeLibrary**和**LoadLibrary**) 如果您的應用程式使用多個執行緒。 使用`AfxLoadLibrary`和`AfxFreeLibrary`可確保載入及卸載 DLL 的延伸模組而損毀全域 MFC 狀態時執行的啟動和關閉程式碼。  
  
### <a name="example"></a>範例  
 請參閱範例的[AfxLoadLibrary](#afxloadlibrary)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdll_.h  
  
##  <a name="afxgetapp"></a>AfxGetApp  
 這個函式所傳回的指標可以用來存取應用程式的資訊，例如主要的訊息分派程式碼或最上層視窗。  
  
```   
CWinApp* AFXAPI AfxGetApp(); 
```  
  
### <a name="return-value"></a>傳回值  
 指向單一`CWinApp`應用程式的物件。  
  
### <a name="remarks"></a>備註  
 如果這個方法會傳回 NULL，則可能表示，應用程式主視窗有尚未完全初始化。 它也可能表示有問題。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxgetappname"></a>AfxGetAppName  
 這個函式傳回的字串可以用於診斷訊息或者用作暫存字串名稱的根。  
  
```   
LPCTSTR AFXAPI AfxGetAppName(); 
```  
  
### <a name="return-value"></a>傳回值  
 包含應用程式名稱的 NULL 結尾字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxgetinstancehandle"></a>AfxGetInstanceHandle  
 這個函式可讓您擷取目前應用程式的執行個體控制代碼。  
  
```   
HINSTANCE  AFXAPI AfxGetInstanceHandle(); 
```  
  
### <a name="return-value"></a>傳回值  
 應用程式目前執行個體的 `HINSTANCE`。 如果是從與 MFC 的 USRDLL 版本連結的 DLL 中呼叫，則會傳回 DLL 的 `HINSTANCE`。  
  
### <a name="remarks"></a>備註  
 除非是從與 MFC 的 USRDLL 版本連結的 DLL 中呼叫，否則 `AfxGetInstanceHandle` 一定會傳回可執行檔 (.EXE) 的 `HINSTANCE`。 在此種狀況下，它會傳回 DLL 的 `HINSTANCE`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxgetmainwnd"></a>AfxGetMainWnd  
 如果您的應用程式是 OLE 伺服器，呼叫此函式可擷取而不是直接參考應用程式的現用主視窗的指標[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)應用程式物件的成員。  
  
```   
CWnd* AFXAPI AfxGetMainWnd(); 
```  
  
### <a name="return-value"></a>傳回值  
 如果伺服器具有在容器內就地使用中的物件，且此容器也正在使用中，則此函式會傳回包含就地使用中文件的框架視窗物件的指標。  
  
 如果容器內沒有任何就地使用中的物件，或者應用程式並非 OLE 伺服器，則此函式只會傳回應用程式物件的 `m_pMainWnd`。  
  
 如果從應用程式的主執行緒呼叫 `AfxGetMainWnd`，則它會根據上述規則傳回應用程式的主視窗。 如果從應用程式的次要執行緒呼叫函式時，則函式會傳回與發出呼叫的執行緒關聯的主視窗。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式不是 OLE 伺服器，則呼叫此函式和直接參考應用程式物件的 `m_pMainWnd` 成員的功用相同。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration  
 使用此函數來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** ( **HKCU**) 節點。  
  
```  
BOOL AFXAPI AfxGetPerUserRegistration();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`指出登錄資訊的重新導向至**HKCU**節點。`FALSE`表示，應用程式登錄資訊寫入預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** ( **HKCR**)。  
  
### <a name="remarks"></a>備註  
 如果您啟用登錄重新導向時，架構會將重新導向從存取**HKCR**至**HKEY_CURRENT_USER\Software\Classes**。 僅適用的 MFC 和 ATL 架構會受到重新導向。  
  
 若要變更是否要應用程式將登錄存取重新導向，使用[AfxSetPerUserRegistration](#afxsetperuserregistration)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxstat_.h    
  
##  <a name="afxgetresourcehandle"></a>AfxGetResourceHandle  
 使用`HINSTANCE`應用程式的資源直接存取，例如，對 Windows 函式中呼叫此函數所傳回的控制代碼**FindResource**。  
  
```   
extern HINSTANCE  AfxGetResourceHandle(); 
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`控制代碼的應用程式的預設資源的載入位置。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxgetthread"></a>AfxGetThread  
 呼叫此函式可取得的指標[CWinThread](../../mfc/reference/cwinthread-class.md)物件，代表目前執行中執行緒。  
  
```   
CWinThread* AfxGetThread(); 
```  
  
### <a name="return-value"></a>傳回值  
 目前正在執行的執行緒; 的指標否則**NULL**。  
  
### <a name="remarks"></a>備註  
 必須從所需的執行緒內呼叫。  
  
> [!NOTE]
>  如果您要移植 MFC 專案呼叫`AfxGetThread`Visual c + + 版本 4.2、 5.0 或 6.0 中，從`AfxGetThread`呼叫[AfxGetApp](#afxgetapp)如果不找到任何執行緒。 在 Visual c +.NET 和更新版本，`AfxGetThread`傳回**NULL**如果找不到任何執行緒。 如果您要應用程式執行緒，則必須呼叫 `AfxGetApp`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxinitrichedit"></a>AfxInitRichEdit  
 呼叫此函式來初始化應用程式的 rich edit 控制項 （1.0 版）。  
  
```   
BOOL AFXAPI AfxInitRichEdit(); 
```  
  
### <a name="remarks"></a>備註  
 此函式會提供回溯相容性。 建立 Visual c + +.NET 和更新版本使用的應用程式[AfxInitRichEdit2](#afxinitrichedit2)。  
  
 `AfxInitRichEdit`載入 RICHED32。初始化 1.0 版的 rich edit 控制項的 DLL。 若要使用版本 2.0 和 3.0 的 rich edit 控制項，RICHED20。需要載入 DLL。 這是藉由呼叫[AfxInitRichEdit2](#afxinitrichedit2)。 如果您有 Visual c + +.NET 前已建立的 rich edit 控制項的對話方塊資源，豐富的編輯控制項的自動版本 1.0。 使用 Visual c + +.NET 資源編輯器中插入的豐富編輯控制項是 2.0 版。  
  
 若要更新現有的 Visual c + + 應用程式用於 2.0 版中的豐富編輯控制項，開啟。RC 檔為文字，變更 「 RichEdit20a"從"RICHEDIT 「 每個 rich edit 控制項的類別名稱。 然後取代呼叫`AfxInitRichEdit`與`AfxInitRichEdit2`。  
  
 此函式也會初始化通用控制項程式庫中，如果文件庫尚未初始化處理程序。 如果您直接從 MFC 應用程式使用 rich edit 控制項，您應該呼叫此函式可確保 MFC 已正確初始化豐富的編輯控制項執行階段。 如果您呼叫的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，則通常不需要呼叫此函式，但在某些情況下可能需要。  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxinitrichedit2"></a>AfxInitRichEdit2  
 呼叫此函式以初始化應用程式的 Rich Edit 控制項 (2.0 版和更新版本)。  
  
```   
BOOL AFXAPI AfxInitRichEdit2(); 
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式以載入 RICHED20.DLL 和初始化 2.0 版的 Rich Edit 控制項。 如果您呼叫的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，則通常不需要呼叫此函式，但在某些情況下可能需要。  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  

  ## <a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass
判斷指定的視窗是否為擴充框架物件。  
   
### <a name="syntax"></a>語法    
```  
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );  
```
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 從 `CWnd`衍生之物件的指標。  
   
### <a name="return-value"></a>傳回值  
 `TRUE`如果提供的視窗是擴充的框架物件，否則`FALSE`。  
   
### <a name="remarks"></a>備註  
 如果 `TRUE` 衍生自下列其中一個類別，此方法會傳回 `pWnd` ：  
  
-   `CFrameWndEx`  
  
-   `CMDIFrameWndEx`  
  
-   `COleIPFrameWndEx`  
  
-   `COleDocIPFrameWndEx`  
  
-   `CMDIChildWndEx`  
  
 當您必須驗證函式或方法參數是否為擴充框架物件時，此方法很有用。  
   
### <a name="requirements"></a>需求  
 **Header:** afxpriv.h  
   
### <a name="see-also"></a>另請參閱  
 [CWnd 類別](cwnd-class.md)   
 [CFrameWndEx 類別](cframewndex-class.md)   

## <a name="afxismfctoolbar"></a>AfxIsMFCToolBar
判斷指定的視窗是否為工具列物件。  
   
### <a name="syntax"></a>語法    
```  
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);  
```
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 從 `CWnd`衍生之物件的指標。  
   
### <a name="return-value"></a>傳回值  
 如果提供的視窗是工具列物件為 `TRUE`；否則為 `FALSE`。  
   
### <a name="remarks"></a>備註  
 如果 `TRUE` 衍生自 `pWnd`，這個方法會傳回 `CMFCToolBar`。 當您必須驗證函式或方法參數是否為 `CMFCToolBar` 物件時，這個方法就很有用。  
   
### <a name="requirements"></a>需求  
 **Header:** afxpriv.h  
   
### <a name="see-also"></a>另請參閱  
 [CWnd 類別](cwnd-class.md)   
 [CMFCToolBar 類別](cmfctoolbar-class.md)

 
## <a name="afxkeyboardmanager"></a>AfxKeyboardManager
指標的全域[鍵盤管理員](ckeyboardmanager-class.md)。  
   
### <a name="syntax"></a>語法    
```  
CKeyboardManager* afxKeyboardManager;  
```  
### <a name="requirements"></a>需求  
 **標頭︰** afxkeyboardmanager.h  
   
### <a name="see-also"></a>另請參閱  

 [巨集、 全域函式和全域變數](mfc-macros-and-globals.md)   
 [CKeyboardManager 類別](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>AfxLoadLibrary  
 使用 `AfxLoadLibrary` 對應 DLL 模組。  
  
```   
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName); 
```  
  
### <a name="parameters"></a>參數  
 *lpszModuleName*  
 指向以 null 終止的字串，其中包含的模組名稱 (其中一個。DLL 或。EXE 檔案）。 指定的名稱是模組的檔案名稱。  
  
 如果字串中指定的路徑，但檔案不存在指定的目錄中，函式會失敗。  
  
 如果未指定路徑和檔名的副檔名省略，預設的延伸模組。DLL 會附加。 不過，檔名字串可以包含尾端點字元 （.） 來表示模組名稱並沒有副檔名。 未指定路徑，函式會搜尋下列順序中的檔案︰  
  
-   載入應用程式目錄。  
  
-   目前的目錄。  
  
- **Windows 95/98:** Windows 系統目錄。 **Windows NT:** 32 位元 Windows 系統目錄。 這個目錄的名稱是 SYSTEM32。  
  
- **只有 Windows NT:** 16 位元 Windows 系統目錄。 取得此目錄的路徑沒有 Win32 函式，但它會搜尋。 這個目錄的名稱是系統。  
  
-   Windows 目錄。  
  
-   在 PATH 環境變數所列的目錄。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是模組的控制代碼。 如果函式失敗，傳回值會是 NULL。  
  
### <a name="remarks"></a>備註  
 它會傳回的控制代碼，可用於[GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212)取得 DLL 函式的位址。 `AfxLoadLibrary`也可以用來將其他可執行模組的對應。  
  
 每個處理序會維護每個載入的程式庫模組的參考計數。 此參考計數會遞增每次`AfxLoadLibrary`呼叫而且每次都會遞減`AfxFreeLibrary`呼叫。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。  
  
 務必使用`AfxLoadLibrary`和`AfxFreeLibrary`(而不是 Win32 函式**LoadLibrary**和**FreeLibrary**) 如果您的應用程式使用多個執行緒，而且它會以動態方式載入擴充 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`確保執行時載入及卸載擴充 DLL 的啟動和關閉程式碼而損毀全域 MFC 狀態。  
  
 使用`AfxLoadLibrary`應用程式中必須要動態連結至 MFC 的 DLL 版本; 的標頭檔`AfxLoadLibrary`，Afxdll_.h，僅包含如果 MFC 連結到 dll 的應用程式。 這是根據設計，因為您必須將連結至 MFC 的 DLL 版本使用或建立擴充 Dll。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_DLLUser # 1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]  
[!code-cpp[NVC_MFC_DLLUser # 2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]  
[!code-cpp[NVC_MFC_DLLUser # 3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxdll_.h  
   
## <a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager
指標的全域[可功能表管理員](cmenutearoffmanager-class.md)。  
   
### <a name="syntax"></a>語法    
```  
CMenuTearOffManager* g_pTearOffMenuManager;  
```  
### <a name="requirements"></a>需求  
 **標頭︰** afxmenutearoffmanager.h  
   
### <a name="see-also"></a>另請參閱     
 [CMenuTearOffManager 類別](cmenutearoffmanager-class.md)
 
## <a name="afxmousemanager"></a>AfxMouseManager
指標的全域[滑鼠管理員](cmousemanager-class.md)。  
   
### <a name="syntax"></a>語法  
  ```  
CMouseManager* afxMouseManager;  
```  
### <a name="requirements"></a>需求  
 **標頭︰** afxmousemanager.h  
   
### <a name="see-also"></a>另請參閱  
 [CMouseManager 類別](cmousemanager-class.md)
 

  
##  <a name="afxregisterclass"></a>AfxRegisterClass  
 使用這個函式在使用 MFC 的 DLL 中登錄視窗類別。  
  
```   
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass); 
```  
  
### <a name="parameters"></a>參數  
 *lpWndClass*  
 指標[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構，其中包含要註冊視窗類別的相關資訊。 如需有關此結構的詳細資訊，請參閱 Windows SDK。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果類別成功登錄，否則為**FALSE**。  
  
### <a name="remarks"></a>備註  
 如果您使用這個函式，類別會在卸載 DLL 時自動解除登錄。  
  
 在非 DLL 組建`AfxRegisterClass`識別項定義為巨集對應至 Windows 函式**RegisterClass**，因為登錄應用程式中的類別會自動解除登錄。 如果您使用`AfxRegisterClass`而不是**RegisterClass**，可以使用您的程式碼，而不需要在應用程式和 DLL 中的變更。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_DLL #3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxregisterwndclass"></a>AfxRegisterWndClass  
 可讓您註冊您的視窗類別。  
  
```  
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,  
    HCURSOR hCursor = 0,  
    HBRUSH hbrBackground = 0,  
    HICON hIcon = 0);  
```  
  
### <a name="parameters"></a>參數  
 *nClassStyle*  
 指定的 Windows 類別樣式或樣式，建立使用位元 OR 組合 ( **|**) 運算子，如視窗類別。 如需類別樣式的清單，請參閱[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) Windows SDK 中的結構。 如果**NULL**，將設定的預設值，如下所示︰  
  
-   將滑鼠樣式設定為**CS_DBLCLKS**，會將按兩下訊息至視窗程序在使用者按兩下滑鼠時。  
  
-   箭號游標樣式設定為 Windows 標準**IDC_ARROW**。  
  
-   若要設定的背景筆刷**NULL**，因此視窗不會清除它的背景。  
  
-   將圖示設定為標準的旗標 Windows 標誌圖示。  
  
 `hCursor`  
 指定將在從視窗類別建立之各個視窗中安裝的游標資源控制代碼。 如果您使用預設值是**0**，您會取得標準**IDC_ARROW**資料指標。  
  
 *hbrBackground*  
 指定將在從視窗類別建立之各個視窗中安裝的筆刷資源控制代碼。 如果您使用預設值是**0**，您必須**NULL**背景筆刷，視窗會您，根據預設，不會清除它的背景處理[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)。  
  
 `hIcon`  
 指定將在從視窗類別建立之各個視窗中安裝的圖示資源控制代碼。 如果您使用預設值是**0**，就會呈現標準的旗標 Windows 標誌圖示。  
  
### <a name="return-value"></a>傳回值  
 包含類別名稱的以 NULL 結尾字串。 您可以傳遞至這個類別名稱**建立**成員函式中的`CWnd`或其他**CWnd-**衍生類別來建立視窗。 此名稱是由 MFC 程式庫所產生。  
  
> [!NOTE]
>  傳回值是靜態緩衝區的指標。 若要儲存此字串，請將它指派給 `CString` 變數。  
  
### <a name="remarks"></a>備註  
 MFC 程式庫會自動為您註冊多個標準視窗類別。 如果您要註冊自己的視窗類別，請呼叫這個函式。  
  
 由 `AfxRegisterWndClass` 為類別註冊的名稱取決於參數的內容。 如果您以相同參數多次呼叫 `AfxRegisterWndClass`，它只會註冊第一次呼叫的類別。 以相同參數對 `AfxRegisterWndClass` 進行的後續呼叫會傳回已註冊的類別名稱。  
  
 如果以相同參數對多個 CWnd 衍生類別呼叫 `AfxRegisterWndClass`，除了取得每個類別的獨立視窗類別之外，每個類別還會共用相同的視窗類別。 這會造成問題，如果**CS_CLASSDC**類別樣式。 除了多個**CS_CLASSDC**視窗類別，您最終會使用一個**CS_CLASSDC**視窗類別，且使用類別共用相同的 DC 的所有 c + + 視窗。 若要避免這個問題，請呼叫[AfxRegisterClass](#afxregisterclass)註冊類別。  
  
 技術提示是指[TN001︰ 視窗類別註冊](../../mfc/tn001-window-class-registration.md)如需有關視窗類別註冊和`AfxRegisterWndClass`函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
  
##  <a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration  
 設定應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。  
  
```  
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`指出登錄資訊的重新導向至**HKCU**節點。`FALSE`表示，應用程式登錄資訊寫入預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** ( **HKCR**)。  
  
### <a name="remarks"></a>備註  
 之前[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，通常存取登錄的應用程式使用**HKEY_CLASSES_ROOT**節點。 不過，在使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，您必須在提高權限寫入模式中執行應用程式**HKCR**。  
  
 這個方法可讓您的應用程式來讀取和寫入登錄，但不執行提高權限模式中，將登錄存取重新導向至**HKCR**至**HKCU**。 如需詳細資訊，請參閱[連結器屬性頁](../../ide/linker-property-pages.md)。  
  
 如果您啟用登錄重新導向時，架構會將重新導向從存取**HKCR**至**HKEY_CURRENT_USER\Software\Classes**。 僅適用的 MFC 和 ATL 架構會受到重新導向。  
  
 預設實作會存取下的登錄**HKCR**。  
  
### <a name="requirements"></a>需求  
  **標頭**afxstat_.h    
  
##  <a name="afxsetresourcehandle"></a>AfxSetResourceHandle  
 使用此函式設定 `HINSTANCE` 控制代碼，決定載入應用程式的預設資源的位置。  
  
```  
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);  
```  
  
### <a name="parameters"></a>參數  
 `hInstResource`  
 載入應用程式的資源的 .EXE 或 DLL 檔的執行個體或模組控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing # 135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxwin.h  

## <a name="afxshellmanager"></a>AfxShellManager
指標的全域[殼層管理員](cshellmanager-class.md)。  
   
### <a name="syntax"></a>語法    
```  
CShellManager* afxShellManager;  
```  

### <a name="requirements"></a>需求  
 **標頭︰** afxshellmanager.h  
   
### <a name="see-also"></a>另請參閱  
 [CShellManager 類別](cshellmanager-class.md)
  
##  <a name="afxsocketinit"></a>AfxSocketInit  
 呼叫此函式您`CWinApp::InitInstance`初始化 Windows Sockets 的覆寫。  
  
```  
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);  
```  
  
### <a name="parameters"></a>參數  
 `lpwsaData`  
 指標[WSADATA](../../mfc/reference/wsadata-structure.md)結構。 如果`lpwsaData`不等於`NULL`的位址`WSADATA`結構會填入呼叫`WSAStartup`。 此函式也可確保`WSACleanup`應用程式終止前，為您呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 當使用靜態連結的 MFC 應用程式中的次要執行緒中的 MFC 通訊端，您必須呼叫`AfxSocketInit`中使用通訊端初始化通訊端程式庫的每個執行緒。 根據預設，`AfxSocketInit`只能在主執行緒中呼叫。  
  
### <a name="requirements"></a>需求  
  **標頭**afxsock.h  

## <a name="afxusertoolsmanager"></a>AfxUserToolsManager
指標的全域[使用者工具管理員](cusertoolsmanager-class.md)。  
   
### <a name="syntax"></a>語法    
```  
CUserToolsManager* afxUserToolsManager;  
```  
   
### <a name="requirements"></a>需求  
 **標頭︰** afxusertoolsmanager.h  
   
### <a name="see-also"></a>另請參閱  
 [CUserToolsManager 類別](cusertoolsmanager-class.md)
 
  
##  <a name="afxwininit"></a>AfxWinInit  
 此函式會呼叫 MFC 提供`WinMain`函式，做為一部分[CWinApp](../../mfc/reference/cwinapp-class.md)的 GUI 型的應用程式，以初始化 MFC 初始化。  
  
```  
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,  
    HINSTANCE hPrevInstance,  
    LPTSTR lpCmdLine,  
    int nCmdShow);  
```  
  
### <a name="parameters"></a>參數  
 `hInstance`  
 目前正在執行的模組控制代碼。  
  
 *hPrevInstance*  
 應用程式的上一個執行個體控制代碼。 Win32 應用程式，這個參數是一律**NULL**。  
  
 `lpCmdLine`  
 指向以 null 終止的字串，指定命令列應用程式。  
  
 `nCmdShow`  
 指定會顯示 GUI 應用程式的主視窗的方式。  
  
### <a name="remarks"></a>備註  
 主控台應用程式，這不會使用 MFC 提供`WinMain`函式，您必須呼叫`AfxWinInit`直接來初始化 MFC。  
  
 如果您呼叫`AfxWinInit`自己，您應該宣告的執行個體`CWinApp`類別。 主控台應用程式中，您可以選擇不衍生您自己從`CWinApp`並改為使用的執行個體`CWinApp`直接。 這項技術是如果您決定要保留您的應用程式的所有功能的實作中適當**主要**。  
  
> [!NOTE]
>  當它建立啟用內容之組件時，MFC 會使用使用者模組所提供的資訊清單資源。 啟用內容可在 `AfxWinInit` 中建立。 如需詳細資訊，請參閱[MFC 模組狀態的啟用內容支援](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_AfxWinInit # 1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]  

### <a name="requirements"></a>需求  
  **標頭**afxwin.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)

