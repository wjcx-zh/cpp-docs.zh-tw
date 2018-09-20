---
title: 應用程式資訊和管理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b64e92eaca38743f0bc9de31f9be7684271c4674
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374347"
---
# <a name="application-information-and-management"></a>應用程式資訊和管理

當您撰寫應用程式時，您會建立單一[CWinApp](../../mfc/reference/cwinapp-class.md)-衍生物件。 有時候，您可能想要取得此物件來自外部的相關資訊`CWinApp`-衍生物件。 或者，您可能需要其他全域"mananger 」 物件的存取權。

Microsoft Foundation Class Library 會提供下列全域函式，可協助您完成這些工作：

### <a name="application-information-and-management-functions"></a>應用程式資訊和管理功能

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|建立新的執行緒。|
|[AfxContextMenuManager](#afxcontextmenumanager)|指標的全域[操作功能表管理員](ccontextmenumanager-class.md)。|
|[AfxEndThread](#afxendthread)|終止目前的執行緒。|
|[AfxFindResourceHandle](#afxfindresourcehandle)|將逐步引導資源鏈結並找出特定資源的資源識別碼和資源類型。 |
|[AfxFreeLibrary](#afxfreelibrary)|載入的動態連結程式庫 (DLL) 模組; 的遞減參考計數當參考計數到達零時，此模組就會是未對應。|
|[AfxGetApp](#afxgetapp)|傳回指向應用程式的單一`CWinApp`物件。|
|[AfxGetAppName](#afxgetappname)|傳回字串，包含應用程式的名稱。|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|傳回表示這個執行個體，應用程式的 HINSTANCE。|
|[AfxGetMainWnd](#afxgetmainwnd)|讓指標回到目前的 「 主要 」 視窗非 OLE 應用程式或伺服器應用程式的就地框架視窗。|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函式來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** ( **HKCU**) 節點。|
|[AfxGetResourceHandle](#afxgetresourcehandle)|傳回 HINSTANCE 來源的應用程式的預設資源。 您可以使用這來直接存取應用程式的資源。|
|[AfxGetThread](#afxgetthread)|擷取目前的指標[CWinThread](../../mfc/reference/cwinthread-class.md)物件。|
|[AfxInitRichEdit](#afxinitrichedit)|初始化 1.0 的 rich edit 控制項的應用程式的版本。|
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化 2.0 和更新版本的 rich edit 控制項的應用程式的版本。|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|判斷指定的視窗是否為擴充框架物件。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|判斷指定的視窗是否為工具列物件。|
|[AfxKeyboardManager](#afxkeyboardmanager)|指標的全域[鍵盤管理員](ckeyboardmanager-class.md)。|
|[AfxLoadLibrary](#afxloadlibrary)|對應 DLL 模組，並傳回的控制代碼，可用來取得 DLL 函式的位址。|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|指標的全域[可更換功能表管理員](cmenutearoffmanager-class.md)。|
|[AfxMouseManager](#afxmousemanager)|指標的全域[滑鼠管理員](cmousemanager-class.md)。|
|[AfxRegisterClass](#afxregisterclass)|註冊視窗類別中使用 MFC 的 DLL。|
|[AfxRegisterWndClass](#afxregisterwndclass)|註冊以補充那些由 MFC 自動註冊的 Windows 視窗類別。|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|設定應用程式重新導向登錄存取權是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|
|[AfxSetResourceHandle](#afxsetresourcehandle)|設定 HINSTANCE 控制代碼的預設資源的應用程式載入的位置。|
|[AfxShellManager](#afxshellmanager)|指標的全域[殼層管理員](cshellmanager-class.md)。 |
|[AfxSocketInit](#afxsocketinit)|在呼叫`CWinApp::InitInstance`覆寫，以初始化 Windows 通訊端。|
|[AfxUserToolsManager](#afxusertoolsmanager)|指標的全域[使用者工具管理員](cusertoolsmanager-class.md)。|
|[AfxWinInit](#afxwininit)|由 MFC 提供呼叫`WinMain`函式，做為一部分[CWinApp](../../mfc/reference/cwinapp-class.md)以 GUI 為基礎的應用程式，以初始化 MFC 初始化。 必須針對使用 MFC 的主控台應用程式的直接呼叫。|



##  <a name="afxbeginthread"></a>  AfxBeginThread

呼叫此函式來建立新的執行緒。

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

*pfnThreadProc*<br/>
指向背景工作執行緒的控制函式。 不可以是 NULL。 此函式必須宣告，如下所示：

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
物件的 RUNTIME_CLASS 衍生自[CWinThread](../../mfc/reference/cwinthread-class.md)。

*pParam*<br/>
要傳遞至控制函式中的函式宣告的參數中所示的參數*pfnThreadProc*。

*nPriority*<br/>
想要的執行緒優先權。 如需完整清單和描述可用的優先順序，請參閱[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

*nStackSize*<br/>
指定的大小，以位元組為單位的新執行緒的堆疊。 如果為 0，則堆疊大小就會預設堆疊大小相同與建立的執行緒。

*dwCreateFlags*<br/>
指定其他旗標控制執行緒的建立。 這個旗標可以包含兩個值之一：

- CREATE_SUSPENDED 啟動執行緒以暫停計數之一。 如果您想要初始化的任何成員資料，請使用 CREATE_SUSPENDED`CWinThread`物件，例如[create_suspended](../../mfc/reference/cwinthread-class.md#m_bautodelete)或衍生類別中，執行緒開始執行之前的任何成員。 您的初始化完成之後，使用[cwinthread:: Resumethread](../../mfc/reference/cwinthread-class.md#resumethread)開始執行的執行緒。 執行緒將不會執行直到`CWinThread::ResumeThread`呼叫。

- **0**在建立後立即啟動執行緒。

*lpSecurityAttrs*<br/>
指向[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)結構，指定執行緒的安全性屬性。 如果是 NULL，就會使用相同的安全性屬性建立的執行緒。 如需有關此結構的詳細資訊，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

新建立的執行緒物件或如果發生失敗則為 NULL 指標。

### <a name="remarks"></a>備註

第一種形式的`AfxBeginThread`建立背景工作執行緒。 第二個形式會建立可為使用者介面執行緒或背景工作執行緒。

`AfxBeginThread` 建立新`CWinThread`物件時，會呼叫其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函式以開始執行執行緒，並傳回執行緒的指標。 整個程序進行檢查以確定所有物件都是已解除配置正確建立的任何部分萬一失敗。 若要結束執行緒，呼叫[AfxEndThread](#afxendthread)從內的執行緒或從背景工作執行緒的控制函式傳回。

必須由應用程式啟用多執行緒否則，此函式會失敗。 如需有關如何啟用多執行緒的詳細資訊，請參閱[/MD、 /MT、 /LD （使用執行階段程式庫）](../../build/reference/md-mt-ld-use-run-time-library.md)下方*Visual c + + 編譯器選項*。

如需詳細資訊`AfxBeginThread`，請參閱文章[多執行緒： 建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)並[多執行緒： 建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)。

### <a name="example"></a>範例

範例，請參閱[csocket:: Attach](../../mfc/reference/csocket-class.md#attach)。

### <a name="requirements"></a>需求

  **標頭**afxwin.h

## <a name="afxcontextmenumanager"></a> AfxContextMenuManager

指標的全域[操作功能表管理員](ccontextmenumanager-class.md)。

### <a name="syntax"></a>語法

```
CContextMenuManager* afxContextMenuManager;
```
### <a name="requirements"></a>需求

**標頭：** afxcontextmenumanager.h

### <a name="see-also"></a>另請參閱

[CContextMenuManager 類別](ccontextmenumanager-class.md)


##  <a name="afxendthread"></a>  AfxEndThread

呼叫此函式可終止目前正在執行的執行緒。

```
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>參數

*nExitCode*<br/>
指定執行緒的結束代碼。

*bDelete*<br/>
從記憶體刪除執行緒物件。

### <a name="remarks"></a>備註

必須從內呼叫的執行緒終止。

如需詳細資訊`AfxEndThread`，請參閱文章[多執行緒： 結束執行緒](../../parallel/multithreading-terminating-threads.md)。

### <a name="requirements"></a>需求

  **標頭**afxwin.h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
使用 `AfxFindResourceHandle` 查核資源鏈結並依資源 ID 和資源類型尋找特定的資源。

### <a name="syntax"></a>語法

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```
### <a name="parameters"></a>參數

*lpszName*<br/>
包含資源 ID 之字串的指標。
*lpszType*<br/>
資源類型的指標。 如需資源類型的清單，請參閱 < [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) Windows SDK 中。

### <a name="return-value"></a>傳回值

包含資源之模組的控制代碼。

### <a name="remarks"></a>備註

`AfxFindResourceHandle` 會尋找特定資源並將控制代碼傳回到包含資源的模組。 資源可能會在任何 MFC 延伸模組已載入的 DLL。 `AfxFindResourceHandle` 會告知您哪一個 DLL 中內含資源。

模組會依此順序搜尋：

1. 主要模組 （如果它是 MFC 擴充 DLL）。

1. 非系統模組。

1. 特定語言的模組。

1. 主要模組 (如果它是系統 DLL)。

1. 系統模組。

### <a name="requirements"></a>需求

**標題:** afxwin.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)

##  <a name="afxfreelibrary"></a>  AfxFreeLibrary

`AfxFreeLibrary` 和 `AfxLoadLibrary` 會保留每個載入的程式庫模組的參考計數。

```
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>參數

*hInstLib*<br/>
所載入程式庫模組的控制代碼。 [AfxLoadLibrary](#afxloadlibrary)傳回這個控制代碼。

### <a name="return-value"></a>傳回值

如果函式成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

`AfxFreeLibrary` 會將載入的動態連結程式庫 (DLL) 模組的參考計數遞減。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。 每次呼叫 `AfxLoadLibrary` 時，此參考計數會遞增。

在取消對應程式庫模組之前，系統會啟用 DLL 來中斷處理序使用它的連結。 這樣做可讓 DLL 代表目前的處理序清除已配置的資源。 在進入點函式傳回之後，程式庫模組就會從目前處理序的位址空間中移除。

使用 `AfxLoadLibrary` 對應 DLL 模組。

請務必使用`AfxFreeLibrary`並`AfxLoadLibrary`(而不是 Win32 函式`FreeLibrary`和`LoadLibrary`) 如果您的應用程式使用多個執行緒。 使用`AfxLoadLibrary`和`AfxFreeLibrary`可確保當載入及卸載 DLL 的 MFC 延伸模組不會不會損毀的通用的 MFC 狀態時執行的啟動和關閉程式碼。

### <a name="example"></a>範例

範例，請參閱[AfxLoadLibrary](#afxloadlibrary)。

### <a name="requirements"></a>需求

  **標頭**afxdll_.h

##  <a name="afxgetapp"></a>  AfxGetApp

此函式所傳回的指標，可用來存取應用程式的資訊，例如主要的訊息分派的程式碼或最上層視窗。

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>傳回值

指向單一`CWinApp`應用程式的物件。

### <a name="remarks"></a>備註

如果這個方法會傳回 NULL，則可能表示，應用程式主視窗有尚未完全初始化。 它也可能表示有問題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxgetappname"></a>  AfxGetAppName

這個函式傳回的字串可以用於診斷訊息或者用作暫存字串名稱的根。

```
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>傳回值

包含應用程式名稱的 NULL 結尾字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxgetinstancehandle"></a>  AfxGetInstanceHandle

這個函式可讓您擷取目前應用程式的執行個體控制代碼。

```
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>傳回值

目前的執行個體，應用程式的 HINSTANCE。 如果從與 MFC 的 USRDLL 版本連結的 DLL 內呼叫，則會傳回 dll HINSTANCE。

### <a name="remarks"></a>備註

`AfxGetInstanceHandle` 一律會傳回可執行檔的 HINSTANCE (。EXE) 除非它從呼叫 MFC 的 USRDLL 版本連結的 DLL。 在此情況下，它會傳回 HINSTANCE dll。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd

如果您的應用程式是 OLE 伺服器，呼叫此函式可擷取應用程式，而不是直接參考的現用主視窗的指標[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)應用程式物件的成員。

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>傳回值

如果伺服器具有在容器內就地使用中的物件，且此容器也正在使用中，則此函式會傳回包含就地使用中文件的框架視窗物件的指標。

如果不是就地啟用作用中的容器內的物件，或您的應用程式不是 OLE 伺服器，此函式只會傳回*m_pMainWnd*應用程式物件。

如果從應用程式的主執行緒呼叫 `AfxGetMainWnd`，則它會根據上述規則傳回應用程式的主視窗。 如果從應用程式的次要執行緒呼叫函式時，則函式會傳回與發出呼叫的執行緒關聯的主視窗。

### <a name="remarks"></a>備註

如果您的應用程式不是 OLE 伺服器，則呼叫此函式相當直接參考*m_pMainWnd*應用程式物件的成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxgetperuserregistration"></a>  AfxGetPerUserRegistration

使用此函式來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** ( **HKCU**) 節點。

```
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>傳回值

TRUE 表示登錄資訊會導向至在 HKCU 的節點FALSE 表示，應用程式會將登錄資訊寫入至預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** ( **HKCR**)。

### <a name="remarks"></a>備註

如果您啟用登錄重新導向時，架構會將重新導向存取權**HKCR**要**HKEY_CURRENT_USER\Software\Classes**。 只有 MFC 和 ATL 架構會受到重新導向。

若要變更是否應用程式將登錄存取重新導向，請使用[AfxSetPerUserRegistration](#afxsetperuserregistration)。

### <a name="requirements"></a>需求

  **標頭**afxstat_.h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle

應用程式的資源直接存取，此函數所傳回的 HINSTANCE 處理的使用，例如在呼叫 Windows 函式`FindResource`。

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>傳回值

預設資源的應用程式載入的位置 HINSTANCE 控制代碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxgetthread"></a>  AfxGetThread

呼叫此函式可取得的指標[CWinThread](../../mfc/reference/cwinthread-class.md)物件，表示目前執行中執行緒。

```
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>傳回值

目前執行中執行緒; 指標否則為 NULL。

### <a name="remarks"></a>備註

必須從所需的執行緒內呼叫。

> [!NOTE]
>  如果您要移植 MFC 專案呼叫`AfxGetThread`Visual c + + 版本 4.2、 5.0 或 6.0 中，從`AfxGetThread`呼叫[AfxGetApp](#afxgetapp)如果不找到任何執行緒。 在較新版本的編譯器，`AfxGetThread`如果找不到任何執行緒，則傳回 NULL。 如果您要應用程式執行緒，則必須呼叫 `AfxGetApp`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxinitrichedit"></a>  AfxInitRichEdit

呼叫此函式來初始化應用程式的 rich edit 控制項 （1.0 版）。

```
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>備註

此函式會提供回溯相容性。 新的應用程式應該改用[AfxInitRichEdit2](#afxinitrichedit2)。

`AfxInitRichEdit` 載入 RICHED32。若要初始化 1.0 版的 rich edit 控制項的 DLL。 若要使用版本 2.0 和 3.0 版的 rich edit 控制項，RICHED20。需要載入 DLL。 這是藉由呼叫[AfxInitRichEdit2](#afxinitrichedit2)。

若要更新現有的 Visual c + + 應用程式，以 2.0 版中的豐富編輯控制項，開啟。RC 的檔案，做為文字，變更 「 RichEdit20a"從"RICHEDIT 」 每個 rich edit 控制項的類別名稱。 然後呼叫取代`AfxInitRichEdit`與`AfxInitRichEdit2`。

此函式也會初始化通用控制項程式庫中，如果文件庫尚未初始化處理程序。 如果您直接從 MFC 應用程式使用 rich edit 控制項，您應該呼叫此函式可確保 MFC 已正確初始化豐富編輯控制項執行階段。 如果您呼叫的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，您通常不需要呼叫此函式，但在某些情況下可能必要。

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2

呼叫此函式以初始化應用程式的 Rich Edit 控制項 (2.0 版和更新版本)。

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>備註

呼叫此函式以載入 RICHED20.DLL 和初始化 2.0 版的 Rich Edit 控制項。 如果您呼叫的 Create 方法[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)， [CRichEditView](../../mfc/reference/cricheditview-class.md)，或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，您通常不需要呼叫此函式，但在某些情況下可能必要。

### <a name="requirements"></a>需求

  **標頭**afxwin.h

  ## <a name="afxisextendedframeclass"></a>  AfxIsExtendedFrameClass
判斷指定的視窗是否為擴充框架物件。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```
### <a name="parameters"></a>參數

*pWnd*<br/>
[in]衍生自物件的指標`CWnd`。

### <a name="return-value"></a>傳回值

如果提供的視窗是擴充的框架物件，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳回 TRUE，如果*pWnd*衍生自下列類別之一：

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

當您必須驗證函式或方法參數是否為擴充框架物件時，此方法很有用。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

### <a name="see-also"></a>另請參閱

[CWnd 類別](cwnd-class.md)<br/>
[CFrameWndEx 類別](cframewndex-class.md)

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar

判斷指定的視窗是否為工具列物件。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```
### <a name="parameters"></a>參數

*pWnd*<br/>
[in]衍生自物件的指標`CWnd`。

### <a name="return-value"></a>傳回值

如果提供的視窗是工具列物件，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳回`TRUE`如果*pWnd*衍生自`CMFCToolBar`。 當您必須驗證函式或方法參數是否為 `CMFCToolBar` 物件時，這個方法就很有用。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

### <a name="see-also"></a>另請參閱

[CWnd 類別](cwnd-class.md)<br/>
[CMFCToolBar 類別](cmfctoolbar-class.md)


## <a name="afxkeyboardmanager"></a> AfxKeyboardManager

指標的全域[鍵盤管理員](ckeyboardmanager-class.md)。

### <a name="syntax"></a>語法

```
CKeyboardManager* afxKeyboardManager;
```
### <a name="requirements"></a>需求

**標頭：** afxkeyboardmanager.h

### <a name="see-also"></a>另請參閱

[巨集、 全域函式和全域變數](mfc-macros-and-globals.md)<br/>
[CKeyboardManager 類別](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary

使用 `AfxLoadLibrary` 對應 DLL 模組。

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>參數

*lpszModuleName*<br/>
指向以 null 終止的字串，其中包含的模組名稱 (其中一個。DLL 或。EXE 檔案）。 指定的名稱是模組的檔案名稱。

如果字串中指定的路徑，但檔案不存在於指定的目錄，函式就會失敗。

如果未指定路徑和檔名的副檔名省略，預設的延伸模組。會附加 DLL。 不過，檔名字串可以包含尾端點字元 （.） 來表示模組名稱具有不含副檔名。 指定沒有路徑時，函式會搜尋下列序列中的檔案：

- 從中載入應用程式的目錄。

- 目前的目錄。

- **Windows 95/98:** Windows 系統目錄。 **Windows NT:** 32 位元 Windows 系統目錄。 這個目錄的名稱是 SYSTEM32。

- **只有 Windows NT:** 16 位元 Windows 系統目錄。 取得此目錄中，路徑的 Win32 函式，但它會搜尋。 這個目錄的名稱是系統。

- Windows 目錄中。

- 在 PATH 環境變數所列的目錄。

### <a name="return-value"></a>傳回值

如果此函數成功，則傳回的值會是模組的控制代碼。 如果函式失敗，傳回的值會是 NULL。

### <a name="remarks"></a>備註

它會傳回可用於控制代碼[GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212)取得 DLL 函式的位址。 `AfxLoadLibrary` 也可以用來對應其他可執行檔的模組。

每個處理序會維護每個載入的程式庫模組的參考計數。 此參考計數會遞增每次`AfxLoadLibrary`呼叫，以及每次都會遞減`AfxFreeLibrary`呼叫。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。

請務必使用`AfxLoadLibrary`並`AfxFreeLibrary`(而不是 Win32 函式`LoadLibrary`和`FreeLibrary`) 如果您的應用程式使用多個執行緒，而且它會以動態方式載入 MFC 擴充 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`確保執行載入和卸載 MFC 擴充 DLL 時的啟動和關閉程式碼不損毀的通用的 MFC 狀態。

使用`AfxLoadLibrary`應用程式中必須要以動態方式連結至 MFC 的 DLL 版本; 的標頭檔`AfxLoadLibrary`，Afxdll_.h，只會包含連結 MFC DLL 的應用程式。 這是根據設計，因為您有連結至使用或建立 MFC 擴充 Dll 的 MFC 的 DLL 版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdll_.h

## <a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager

指標的全域[可更換功能表管理員](cmenutearoffmanager-class.md)。

### <a name="syntax"></a>語法

```
CMenuTearOffManager* g_pTearOffMenuManager;
```
### <a name="requirements"></a>需求

**標頭：** afxmenutearoffmanager.h

### <a name="see-also"></a>另請參閱

[CMenuTearOffManager 類別](cmenutearoffmanager-class.md)

## <a name="afxmousemanager"></a>  AfxMouseManager

指標的全域[滑鼠管理員](cmousemanager-class.md)。

### <a name="syntax"></a>語法

```
CMouseManager* afxMouseManager;
```
### <a name="requirements"></a>需求

**標頭：** afxmousemanager.h

### <a name="see-also"></a>另請參閱

[CMouseManager 類別](cmousemanager-class.md)



##  <a name="afxregisterclass"></a>  AfxRegisterClass

使用這個函式在使用 MFC 的 DLL 中登錄視窗類別。

```
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>參數

*lpWndClass*<br/>
指標[WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)結構，其中包含要註冊視窗類別的相關資訊。 如需有關此結構的詳細資訊，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

如果成功註冊的類別;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

如果您使用這個函式，類別會在卸載 DLL 時自動解除登錄。

在非 DLL 組建`AfxRegisterClass`識別項定義為巨集對應至 Windows 函式， `RegisterClass`，因為在應用程式中註冊的類別會自動解除登錄。 如果您使用`AfxRegisterClass`而不是`RegisterClass`，您的程式碼可以使用而不需要在應用程式和 DLL 中的變更。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass

可讓您註冊您的視窗類別。

```
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>參數

*nClassStyle*<br/>
指定的 Windows 類別樣式或樣式，建立使用位元 OR 組合 ( **&#124;**) 運算子，視窗類別。 如需類別樣式的清單，請參閱 < [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) Windows SDK 中的結構。 如果是 NULL，預設值將，如下所示：

- 將滑鼠樣式設定為 CS_DBLCLKS，會將按兩下訊息至視窗程序當使用者按兩下滑鼠。

- 設定 Windows 標準 IDC_ARROW 的箭號游標樣式。

- 設定為 NULL 時，背景筆刷，讓視窗不會清除其背景。

- 將圖示設定為標準的旗標 Windows 標誌圖示。

*hCursor*<br/>
指定將在從視窗類別建立之各個視窗中安裝的游標資源控制代碼。 如果您使用預設值是**0**，您會收到標準 IDC_ARROW 游標。

*hbrBackground*<br/>
指定將在從視窗類別建立之各個視窗中安裝的筆刷資源控制代碼。 如果您使用預設值是**0**，您會有 NULL 背景筆刷，和您的視窗，根據預設，不會清除其背景工作，而處理[WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd)。

*hIcon*<br/>
指定將在從視窗類別建立之各個視窗中安裝的圖示資源控制代碼。 如果您使用預設值是**0**，您會收到標準的旗標 Windows 標誌圖示。

### <a name="return-value"></a>傳回值

包含類別名稱的以 NULL 結尾字串。 您可以傳遞至這個類別名稱`Create`成員函式中的`CWnd`或其他**CWnd-** 衍生的類別建立視窗。 此名稱是由 MFC 程式庫所產生。

> [!NOTE]
>  傳回值是靜態緩衝區的指標。 若要儲存此字串，請將它指派給 `CString` 變數。

### <a name="remarks"></a>備註

MFC 程式庫會自動為您註冊多個標準視窗類別。 如果您要註冊自己的視窗類別，請呼叫這個函式。

由 `AfxRegisterWndClass` 為類別註冊的名稱取決於參數的內容。 如果您以相同參數多次呼叫 `AfxRegisterWndClass`，它只會註冊第一次呼叫的類別。 以相同參數對 `AfxRegisterWndClass` 進行的後續呼叫會傳回已註冊的類別名稱。

如果以相同參數對多個 CWnd 衍生類別呼叫 `AfxRegisterWndClass`，除了取得每個類別的獨立視窗類別之外，每個類別還會共用相同的視窗類別。 如果使用 CS_CLASSDC 類別樣式，這可能會造成問題。 而不是多個 CS_CLASSDC 視窗類別，您得到一個 CS_CLASSDC 視窗類別，並使用該類別共用相同的 DC 的所有 c + + 視窗。 若要避免這個問題，請呼叫[AfxRegisterClass](#afxregisterclass)註冊類別。

請參閱技術附註[TN001： 視窗類別註冊](../../mfc/tn001-window-class-registration.md)如需有關視窗類別註冊和`AfxRegisterWndClass`函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration

設定應用程式重新導向登錄存取權是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。

```
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]TRUE 表示登錄資訊會導向至在 HKCU 的節點FALSE 表示，應用程式會將登錄資訊寫入至預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** ( **HKCR**)。

### <a name="remarks"></a>備註

在 Windows Vista，存取通常會用來登錄應用程式之前**HKEY_CLASSES_ROOT**節點。 不過，Windows Vista 或更新版本的作業系統，您必須執行應用程式將寫入 HKCR 提升權限模式。

這個方法可讓您的應用程式來讀取和寫入登錄，而不需要提高權限模式執行的重新導向從 HKCR HKCU 登錄存取。 如需詳細資訊，請參閱 <<c0> [ 連結器屬性頁](../../ide/linker-property-pages.md)。

如果您啟用登錄重新導向時，架構會將重新導向從 HKCR 來存取**HKEY_CURRENT_USER\Software\Classes**。 只有 MFC 和 ATL 架構會受到重新導向。

預設實作會存取 HKCR 底下的登錄。

### <a name="requirements"></a>需求

  **標頭**afxstat_.h

##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle

您可以使用此函式來設定所決定的預設資源的應用程式載入的位置的 HINSTANCE 控制代碼。

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>參數

*hInstResource*<br/>
載入應用程式的資源的 .EXE 或 DLL 檔的執行個體或模組控制代碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

## <a name="afxshellmanager"></a>  AfxShellManager

指標的全域[殼層管理員](cshellmanager-class.md)。

### <a name="syntax"></a>語法

```
CShellManager* afxShellManager;
```

### <a name="requirements"></a>需求

**標頭：** afxshellmanager.h

### <a name="see-also"></a>另請參閱

[CShellManager 類別](cshellmanager-class.md)

##  <a name="afxsocketinit"></a>  AfxSocketInit

呼叫此函式，您`CWinApp::InitInstance`覆寫，以初始化 Windows 通訊端。

```
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>參數

*lpwsaData*<br/>
指標[WSADATA](../../mfc/reference/wsadata-structure.md)結構。 如果*lpwsaData*不等於 null 值，然後的地址`WSADATA`結構的呼叫所填滿`WSAStartup`。 此函式也可確保`WSACleanup`應用程式終止之前，您會呼叫。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

當使用靜態連結的 MFC 應用程式中的次要執行緒中的 MFC 通訊端，您必須呼叫`AfxSocketInit`中每個執行緒都使用通訊端進行初始化通訊端程式庫。 根據預設，`AfxSocketInit`只在主執行緒中呼叫。

### <a name="requirements"></a>需求

  **標頭**afxsock.h

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager

指標的全域[使用者工具管理員](cusertoolsmanager-class.md)。

### <a name="syntax"></a>語法

```
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>需求

**標頭：** afxusertoolsmanager.h

### <a name="see-also"></a>另請參閱

[CUserToolsManager 類別](cusertoolsmanager-class.md)


##  <a name="afxwininit"></a>  AfxWinInit

由 MFC 提供呼叫此函式`WinMain`函式，做為一部分[CWinApp](../../mfc/reference/cwinapp-class.md)以 GUI 為基礎的應用程式，以初始化 MFC 初始化。

```
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
目前正在執行的模組控制代碼。

*hPrevInstance*<br/>
應用程式的上一個執行個體控制代碼。 是以 Win32 為基礎的應用程式，這個參數是永遠**NULL**。

*lpCmdLine*<br/>
指向以 null 終止的字串，指定命令列應用程式。

*nCmdShow*<br/>
指定會顯示 GUI 應用程式的主視窗的方式。

### <a name="remarks"></a>備註

是主控台應用程式中，這不會使用 MFC 提供`WinMain`函式，您必須呼叫`AfxWinInit`直接以初始化 MFC。

如果您呼叫`AfxWinInit`，您應該宣告的執行個體`CWinApp`類別。 主控台應用程式中，您可以選擇不要將衍生您自己的類別，從`CWinApp`，而使用的執行個體`CWinApp`直接。 這項技術是如果您決定要保留您的應用程式的所有功能的實作中的適當**主要**。

> [!NOTE]
>  當它建立啟用內容組件時，MFC 會使用使用者模組所提供的資訊清單資源。 啟用內容可在 `AfxWinInit` 中建立。 如需詳細資訊，請參閱 < [MFC 模組狀態的啟用內容支援](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxwin.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)
