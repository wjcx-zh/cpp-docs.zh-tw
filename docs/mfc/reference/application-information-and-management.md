---
title: 應用程式資訊和管理
description: 參考 MFC 程式庫 (MFC) 應用程式資訊和管理功能。
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 3412ed3f02e93d3e8c947d4f730355c219493a77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832303"
---
# <a name="application-information-and-management"></a>應用程式資訊和管理

當您撰寫應用程式時，您會建立單一的 [CWinApp](../../mfc/reference/cwinapp-class.md)衍生物件。 有時，您可能會想要從衍生的物件外部取得此物件的相關資訊 `CWinApp` 。 或者，您可能需要存取其他全域「管理員」物件。

MFC 程式庫提供下列全域函式，可協助您完成下列工作：

## <a name="application-information-and-management-functions"></a>應用程式資訊和管理功能

| 名稱 | 描述 |
|-|-|
|[AfxBeginThread](#afxbeginthread)|建立新的執行緒。|
|[AfxCoNtextMenuManager](#afxcontextmenumanager)|全域 [內容功能表管理員](ccontextmenumanager-class.md)的指標。|
|[AfxEndThread](#afxendthread)|終止目前的執行緒。|
|[AfxFindResourceHandle](#afxfindresourcehandle)|引導資源鏈，並依資源識別碼和資源類型找出特定的資源。 |
|[AfxFreeLibrary](#afxfreelibrary)|將已載入動態連結程式庫 (DLL) 模組的參考計數遞減。 當參考計數到達零時，模組就會取消對應。|
|[AfxGetApp](#afxgetapp)|傳回應用程式之單一物件的指標 `CWinApp` 。|
|[AfxGetAppName](#afxgetappname)|傳回包含應用程式名稱的字串。|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|傳回代表此應用程式實例的 HINSTANCE。|
|[AfxGetMainWnd](#afxgetmainwnd)|傳回非 OLE 應用程式目前「主要」視窗的指標，或伺服器應用程式的就地框架視窗。|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|您可以使用此函式來判斷應用程式是否將登錄存取重新導向至 **HKEY_CURRENT_USER** (**HKCU**) 節點。|
|[AfxGetResourceHandle](#afxgetresourcehandle)|將 HINSTANCE 傳回至應用程式的預設資源來源。 用來直接存取應用程式的資源。|
|[AfxGetThread](#afxgetthread)|抓取目前 [CWinThread](../../mfc/reference/cwinthread-class.md) 物件的指標。|
|[AfxInitRichEdit](#afxinitrichedit)|初始化應用程式的1.0 版 rich edit 控制項。|
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化應用程式的2.0 版和更新版本的 rich edit 控制項。|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|判斷指定的視窗是否為擴充框架物件。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|判斷指定的視窗是否為工具列物件。|
|[AfxKeyboardManager](#afxkeyboardmanager)|全域 [鍵盤管理員](ckeyboardmanager-class.md)的指標。|
|[AfxLoadLibrary](#afxloadlibrary)|對應 DLL 模組，並傳回可以用來取得 DLL 函式位址的控制碼。|
|[AfxLoadLibraryEx](#afxloadlibraryex)|使用指定的選項對應 DLL 模組，並傳回可以用來取得 DLL 函式位址的控制碼。|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|全域 [退出功能表管理員](cmenutearoffmanager-class.md)的指標。|
|[AfxMouseManager](#afxmousemanager)|全域 [滑鼠管理員](cmousemanager-class.md)的指標。|
|[AfxRegisterClass](#afxregisterclass)|在使用 MFC 的 DLL 中註冊視窗類別。|
|[AfxRegisterWndClass](#afxregisterwndclass)|註冊 Windows 視窗類別來補充由 MFC 自動註冊的類別。|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|設定應用程式是否將登錄存取重新導向至 **HKEY_CURRENT_USER** (**HKCU**) 節點。|
|[AfxSetResourceHandle](#afxsetresourcehandle)|設定 HINSTANCE 控制碼，以載入應用程式的預設資源。|
|[AfxShellManager](#afxshellmanager)|全域 [shell 管理員](cshellmanager-class.md)的指標。 |
|[AfxSocketInit](#afxsocketinit)|在覆寫中呼叫 `CWinApp::InitInstance` 以初始化 Windows 通訊端。|
|[AfxUserToolsManager](#afxusertoolsmanager)|全域 [使用者工具管理員](cusertoolsmanager-class.md)的指標。|
|[AfxWinInit](#afxwininit)|在 `WinMain` 以 GUI 為基礎的應用程式的 [CWinApp](../../mfc/reference/cwinapp-class.md) 初始化過程中，由 MFC 提供的函式呼叫，以初始化 MFC。 必須直接針對使用 MFC 的主控台應用程式呼叫。|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a> AfxBeginThread

呼叫此函式以建立新的執行緒。

```cpp
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

*pfnThreadProc*\
指向背景工作執行緒的控制函數。 指標不可以是 Null。 此函式必須依照下列方式宣告：

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
衍生自 [CWinThread](../../mfc/reference/cwinthread-class.md)之物件的 RUNTIME_CLASS。

*pParam*\
要傳遞至控制函數的參數。

*nPriority*\
要為執行緒設定的優先順序。 如需可用優先順序的完整清單和描述，請參閱 Windows SDK 中的 [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

*nStackSize*\
指定新執行緒的堆疊大小（以位元組為單位）。 如果為0，則堆疊大小預設為與建立執行緒相同的大小堆疊。

*dwCreateFlags*\
指定控制執行緒建立的其他旗標。 此旗標可以包含下列兩個值的其中一個：

- CREATE_SUSPENDED 啟動暫停計數為1的執行緒。 如果您想要線上程開始執行之前，初始化物件的任何成員資料（ `CWinThread` 例如 [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) 或衍生類別的任何成員），請使用 CREATE_SUSPENDED。 初始化完成之後，請使用 [CWinThread：： ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) 來啟動執行的執行緒。 在呼叫之前，不會執行執行緒 `CWinThread::ResumeThread` 。

- **0** 建立之後立即啟動執行緒。

*lpSecurityAttrs*\
指向指定執行緒之安全性屬性的 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 結構。 如果是 Null，則會使用與建立執行緒相同的安全性屬性。 如需此結構的詳細資訊，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

新建立之執行緒物件的指標，如果發生失敗，則為 Null。

### <a name="remarks"></a>備註

的第一種形式會 `AfxBeginThread` 建立背景工作執行緒。 第二個表單會建立可做為使用者介面執行緒或背景工作執行緒的執行緒。

`AfxBeginThread` 建立新的 `CWinThread` 物件，呼叫其 [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) 函式來開始執行執行緒，並將指標傳回至執行緒。 在整個程式中進行檢查，以確保建立任何部分的物件都能正確解除配置。 若要結束執行緒，請從執行緒內呼叫 [AfxEndThread](#afxendthread) ，或從背景工作執行緒的控制函數返回。

多執行緒必須由應用程式啟用;否則，此函式將會失敗。 如需啟用多執行緒的詳細資訊，請參閱 [/md、/mt、/ld (使用執行時間程式庫) ](../../build/reference/md-mt-ld-use-run-time-library.md)。

如需的詳細資訊 `AfxBeginThread` ，請參閱 [下列文章：多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md) 和 [多執行緒：建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)。

### <a name="example"></a>範例

請參閱 [CSocket：： Attach](../../mfc/reference/csocket-class.md#attach)的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a> AfxCoNtextMenuManager

全域 [內容功能表管理員](ccontextmenumanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>規格需求

**標頭：** afxcoNtextmenumanager。h

## <a name="afxendthread"></a><a name="afxendthread"></a> AfxEndThread

呼叫此函式可終止目前執行中的執行緒。

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>參數

*nExitCode*\
指定執行緒的結束代碼。

*bDelete*\
從記憶體刪除線程物件。

### <a name="remarks"></a>備註

必須從要終止的執行緒內呼叫。

如需的詳細資訊 `AfxEndThread` ，請參閱「 [多執行緒處理：終止執行緒](../../parallel/multithreading-terminating-threads.md)」一文。

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a> AfxFindResourceHandle

使用 `AfxFindResourceHandle` 查核資源鏈結並依資源 ID 和資源類型尋找特定的資源。

### <a name="syntax"></a>語法

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>參數

*lpszName*\
包含資源 ID 之字串的指標。
*lpszType*\
資源類型的指標。 如需資源類型的清單，請參閱 Windows SDK 中的 [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) 。

### <a name="return-value"></a>傳回值

包含資源之模組的控制代碼。

### <a name="remarks"></a>備註

`AfxFindResourceHandle` 尋找特定的資源，並將控制碼傳回至包含資源的模組。 資源可能會在任何載入的 MFC 擴充 DLL 中。 `AfxFindResourceHandle` 會告知您哪一個 DLL 中內含資源。

模組會依此順序搜尋：

1. 主要模組（如果它是 MFC 擴充 DLL）。

1. 非系統模組。

1. 特定語言的模組。

1. 主要模組（如果它是系統 DLL）。

1. 系統模組。

### <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a> AfxFreeLibrary

`AfxFreeLibrary` 和 `AfxLoadLibrary` 會保留每個載入的程式庫模組的參考計數。

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>參數

*hInstLib*\
所載入程式庫模組的控制代碼。 [AfxLoadLibrary](#afxloadlibrary) 會傳回此控制碼。

### <a name="return-value"></a>傳回值

如果函式成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`AfxFreeLibrary` 會將載入的動態連結程式庫 (DLL) 模組的參考計數遞減。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。 每次呼叫 `AfxLoadLibrary` 時，此參考計數會遞增。

在取消對應程式庫模組之前，系統會啟用 DLL 來中斷處理序使用它的連結。 這麼做可讓 DLL 有機會清除配置給目前進程的資源。 在進入點函式傳回之後，程式庫模組就會從目前處理序的位址空間中移除。

使用 `AfxLoadLibrary` 對應 DLL 模組。

`AfxFreeLibrary` `AfxLoadLibrary` `FreeLibrary` `LoadLibrary` 如果您的應用程式使用多個執行緒，請務必使用和 (而不是 Win32 函數和) 。 使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 可確保在 MFC 擴充 DLL 載入和卸載時執行的啟動和關機程式碼，不會損毀全域 mfc 的狀態。

### <a name="example"></a>範例

請參閱 [AfxLoadLibrary](#afxloadlibrary)的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdll_。h

## <a name="afxgetapp"></a><a name="afxgetapp"></a> AfxGetApp

此函式所傳回的指標可用來存取應用程式資訊，例如主要訊息分派程式碼或最上層視窗。

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>傳回值

應用程式之單一物件的指標 `CWinApp` 。

### <a name="remarks"></a>備註

如果這個方法傳回 Null，可能表示應用程式主視窗尚未完全初始化。 這也可能表示有問題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxgetappname"></a><a name="afxgetappname"></a> AfxGetAppName

傳回的字串可用於診斷訊息，或做為暫存字串名稱的根。

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>傳回值

包含應用程式名稱的 NULL 結尾字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a> AfxGetInstanceHandle

這個函式可讓您擷取目前應用程式的執行個體控制代碼。

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>傳回值

應用程式目前實例的 HINSTANCE。 如果從與 MFC 的 USRDLL 版本連結的 DLL 內呼叫，則會傳回 DLL 的 HINSTANCE。

### <a name="remarks"></a>備註

`AfxGetInstanceHandle` 一律會傳回 ( 可執行檔的 HINSTANCE。EXE) 除非是從與 MFC 的 USRDLL 版本連結的 DLL 內呼叫。 在此情況下，它會將 HINSTANCE 傳回至 DLL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a> AfxGetMainWnd

如果您的應用程式是 OLE 伺服器，請呼叫此函式，以取得應用程式的作用中主視窗的指標。 使用此結果，而不是直接參考應用程式物件的 [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) 成員。

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>傳回值

如果伺服器具有在使用中容器內的位置，則會傳回包含就地使用中檔的框架視窗物件指標。

如果容器內沒有就地使用中的物件，或您的應用程式不是 OLE 伺服器，則此函式會傳回應用程式物件的 *m_pMainWnd* 。

如果從應用程式的主執行緒呼叫 `AfxGetMainWnd`，則它會根據上述規則傳回應用程式的主視窗。 如果從應用程式的次要執行緒呼叫函式時，則函式會傳回與發出呼叫的執行緒關聯的主視窗。

### <a name="remarks"></a>備註

如果您的應用程式不是 OLE 伺服器，則呼叫此函式相當於直接參考應用程式物件的 *m_pMainWnd* 成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a> AfxGetPerUserRegistration

您可以使用此函式來判斷應用程式是否將登錄存取重新導向至 **HKEY_CURRENT_USER** (**HKCU**) 節點。

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>傳回值

TRUE 表示登錄資訊會導向至 HKCU 節點。 FALSE 表示應用程式將登錄資訊寫入預設節點。 預設節點是 **HKEY_CLASSES_ROOT** (**HKCR**) 。

### <a name="remarks"></a>備註

如果您啟用登錄重新導向，則架構會將 **HKCR** 的存取重新導向至 **HKEY_CURRENT_USER \software\classes**。 只有 MFC 和 ATL 架構會受到重新導向的影響。

若要變更應用程式是否會重新導向登錄存取，請使用 [AfxSetPerUserRegistration](#afxsetperuserregistration)。

### <a name="requirements"></a>規格需求

  **標頭** afxstat_。h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a> AfxGetResourceHandle

您可以使用此函式所傳回的 HINSTANCE 控制碼，直接存取應用程式的資源，例如，呼叫 Windows 函式 `FindResource` 。

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>傳回值

HINSTANCE 處理應用程式預設資源載入的位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxgetthread"></a><a name="afxgetthread"></a> AfxGetThread

呼叫此函式可取得代表目前執行中線程之 [CWinThread](../../mfc/reference/cwinthread-class.md) 物件的指標。

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>傳回值

目前執行中之執行緒的指標；否則為 NULL。

### <a name="remarks"></a>備註

必須從執行緒內呼叫。

> [!NOTE]
> 如果您要移植 `AfxGetThread` 從 Visual C++ 版本4.2、5.0 或6.0 呼叫的 MFC 專案， `AfxGetThread` 如果找不到任何執行緒，則會呼叫 [AfxGetApp](#afxgetapp) 。 在較新版本的編譯器中， `AfxGetThread` 如果找不到任何執行緒，則會傳回 Null。 如果您要應用程式執行緒，則必須呼叫 `AfxGetApp`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a> AfxInitRichEdit

呼叫此函式以初始化應用程式 (版本 1.0) 的 rich edit 控制項。

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>備註

這是為了回溯相容性而提供的函式。 新的應用程式應該使用 [AfxInitRichEdit2](#afxinitrichedit2)。

`AfxInitRichEdit` 載入 RICHED32.DLL，以初始化 rich edit 控制項的1.0 版。 若要使用 rich edit 控制項的2.0 和3.0 版，RICHED20.DLL 需要載入。 它是透過呼叫 [AfxInitRichEdit2](#afxinitrichedit2)進行載入。

若要將現有 Visual C++ 應用程式中的 rich edit 控制項更新為2.0 版，請開啟。RC 檔做為文字，將每個 rich edit 控制項的類別名稱從 "RICHEDIT" 變更為 "RichEdit20a"。 然後將的呼叫取代 `AfxInitRichEdit` 為 `AfxInitRichEdit2` 。

如果程式庫尚未針對進程初始化，則此函式也會初始化通用控制項程式庫。 如果您直接從 MFC 應用程式使用 rich edit 控制項，請呼叫此函式，以確保 MFC 已正確初始化 rich edit 控制項執行時間。 如果您呼叫 `Create` [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)、 [CRichEditView](../../mfc/reference/cricheditview-class.md)或 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的方法，您通常不需要呼叫此函式，但在某些情況下，可能是必要的。

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a> AfxInitRichEdit2

呼叫此函式以初始化應用程式的 Rich Edit 控制項 (2.0 版和更新版本)。

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>備註

呼叫此函式以載入 RICHED20.DLL 和初始化 2.0 版的 Rich Edit 控制項。 如果您呼叫 `Create` [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)、 [CRichEditView](../../mfc/reference/cricheditview-class.md)或 [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的方法，您通常不需要呼叫此函式，但在某些情況下，可能是必要的。

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a> AfxIsExtendedFrameClass

判斷指定的視窗是否為擴充框架物件。

### <a name="syntax"></a>語法

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>參數

*pWnd*\
在衍生自之物件的指標 `CWnd` 。

### <a name="return-value"></a>傳回值

如果提供的視窗是延伸框架物件，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果 *pWnd* 衍生自下列其中一個類別，則這個方法會傳回 TRUE：

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

當您必須驗證函式或方法參數是否為擴充框架物件時，此方法很有用。

### <a name="requirements"></a>規格需求

**Header:** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a> AfxIsMFCToolBar

判斷指定的視窗是否為工具列物件。

### <a name="syntax"></a>語法

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*\
在衍生自之物件的指標 `CWnd` 。

### <a name="return-value"></a>傳回值

如果提供的視窗是工具列物件，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

`TRUE`如果*pWnd*衍生自，則這個方法會傳回 `CMFCToolBar` 。 當您必須驗證函式或方法參數是否為 `CMFCToolBar` 物件時，這個方法就很有用。

### <a name="requirements"></a>規格需求

**Header:** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a> AfxKeyboardManager

全域 [鍵盤管理員](ckeyboardmanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>規格需求

**標頭：** afxkeyboardmanager。h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a> AfxLoadLibrary

使用 `AfxLoadLibrary` 對應 DLL 模組。

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>參數

*lpszModuleName*\
指向以 null 終止的字串，其中包含模組的名稱 (為。DLL 或。EXE 檔案) 。 指定的名稱是模組的檔案名。

如果字串指定路徑，但檔案不存在於指定的目錄中，則函式會失敗。

如果未指定路徑，且省略副檔名，則為預設副檔名。已附加 DLL。 不過，檔案名字串可包含尾端的點字元 (。 ) 表示模組名稱沒有副檔名。 如果未指定路徑，則函式會使用 [桌面應用程式的搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值會是模組的控制碼。 失敗時，傳回值為 Null。

### <a name="remarks"></a>備註

它會傳回一個控制碼，這個控制碼可在 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 中用來取得 DLL 函式的位址。 `AfxLoadLibrary` 也可以用來對應其他可執行檔模組。

每個進程會維護每個已載入之程式庫模組的參考計數。 每次呼叫時，此參考計數都會遞增 `AfxLoadLibrary` ，並會在每次呼叫時遞減 `AfxFreeLibrary` 。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。

`AfxLoadLibrary` `AfxFreeLibrary` `LoadLibrary` `FreeLibrary` 如果您的應用程式使用多個執行緒，且它會動態載入 MFC 擴充 DLL，請務必使用和 (而不是 Win32 函數和) 。 使用 `AfxLoadLibrary` 並 `AfxFreeLibrary` 確保載入和卸載 MFC 擴充 DLL 時所執行的啟動和關機程式碼，不會損毀全域 mfc 的狀態。

`AfxLoadLibrary`在應用程式中使用，需要您以動態方式連結至 MFC 的 DLL 版本。 `AfxLoadLibrary`只有當 MFC 以 DLL 的形式連結到應用程式時，才會包含 Afxdll_ .h 的標頭檔。 這項需求的設計是因為您必須連結至 MFC 的 DLL 版本，才能使用或建立 MFC 擴充 Dll。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxdll_。h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a> AfxLoadLibraryEx

使用 `AfxLoadLibraryEx` 對應 DLL 模組。

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>參數

*lpFileName*\
指向以 null 終止的字串，其中包含模組的名稱 (為。DLL 或。EXE 檔案) 。 指定的名稱是模組的檔案名。

如果字串指定路徑，但檔案不存在於指定的目錄中，則函式會失敗。

如果未指定路徑，且省略副檔名，則為預設副檔名。已附加 DLL。 不過，檔案名字串可包含尾端的點字元 (。 ) 表示模組名稱沒有副檔名。 如果未指定路徑，則函式會使用 [桌面應用程式的搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

*hFile*\
這個參數保留給未來使用。 它必須是 Null。

*dwFlags*\
載入模組時要採取的動作。 如果未指定旗標，則此函式的行為與函式相同 `AfxLoadLibrary` 。 此參數的可能值會在 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) 檔中說明。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值會是模組的控制碼。 失敗時，傳回值為 Null。

### <a name="remarks"></a>備註

`AfxLoadLibraryEx` 傳回控制碼，這個控制碼可在 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 中用來取得 DLL 函式的位址。 `AfxLoadLibraryEx` 也可以用來對應其他可執行檔模組。

每個進程會維護每個已載入之程式庫模組的參考計數。 每次呼叫時，此參考計數都會遞增 `AfxLoadLibraryEx` ，並會在每次呼叫時遞減 `AfxFreeLibrary` 。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。

`AfxLoadLibraryEx` `AfxFreeLibrary` `LoadLibraryEx` `FreeLibrary` 如果您的應用程式使用多個執行緒，且它會動態載入 MFC 擴充 DLL，請務必使用和 (而不是 Win32 函數和) 。 使用 `AfxLoadLibraryEx` 和 `AfxFreeLibrary` 可確保在 MFC 擴充 DLL 載入和卸載時執行的啟動和關機程式碼，不會損毀全域 mfc 的狀態。

`AfxLoadLibraryEx`在應用程式中使用，需要您以動態方式連結至 MFC 的 DLL 版本。 `AfxLoadLibraryEx`只有當 MFC 以 DLL 的形式連結到應用程式時，才會包含 Afxdll_ .h 的標頭檔。 這項需求的設計是因為您必須連結至 MFC 的 DLL 版本，才能使用或建立 MFC 擴充 Dll。

### <a name="requirements"></a>規格需求

  **標頭** afxdll_。h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager

全域 [退出功能表管理員](cmenutearoffmanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>規格需求

**標頭：** afxmenutearoffmanager。h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a> AfxMouseManager

全域 [滑鼠管理員](cmousemanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>規格需求

**標頭：** afxmousemanager。h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a> AfxRegisterClass

使用這個函式在使用 MFC 的 DLL 中登錄視窗類別。

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>參數

*lpWndClass*\
[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構的指標，其中包含要註冊之視窗類別的相關資訊。 如需此結構的詳細資訊，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

如果類別成功登錄為 TRUE；否則為 FALSE。

### <a name="remarks"></a>備註

如果您使用這個函式，類別會在卸載 DLL 時自動解除登錄。

在非 DLL 組建中， `AfxRegisterClass` 識別碼會定義為對應至 Windows 函式的宏 `RegisterClass` ，因為在應用程式中註冊的類別會自動取消註冊。 如果您使用 `AfxRegisterClass` 而非 `RegisterClass` ，則可以使用您的程式碼，而不需要在應用程式和 DLL 中進行變更。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a> AfxRegisterWndClass

可讓您註冊您的視窗類別。

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>參數

*nClassStyle*\
指定 Windows 類別樣式或樣式的組合（使用位或 (**&#124;**) 運算子）來建立視窗類別。 如需類別樣式的清單，請參閱 Windows SDK 中的 [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) 結構。 如果是 Null，預設值會設定如下：

- 當使用者按兩下滑鼠時，會將按兩下訊息傳送至視窗程序，將滑鼠樣式設定 CS_DBLCLKS。

- 將箭號游標樣式設定為 Windows 標準 IDC_ARROW。

- 將背景筆刷設定為 Null，讓視窗不會清除其背景。

- 將圖示設定為標準的旗標 Windows 標誌圖示。

*hCursor*\
指定將在從視窗類別建立之各個視窗中安裝的游標資源控制代碼。 如果您使用預設值 **0**，則會取得標準 IDC_ARROW 資料指標。

*hbrBackground*\
指定將在從視窗類別建立之各個視窗中安裝的筆刷資源控制代碼。 如果您使用預設值 **0**，則會有 Null 背景筆刷，而且根據預設，您的視窗在處理 [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)時，不會清除其背景。

*hIcon*\
指定將在從視窗類別建立之各個視窗中安裝的圖示資源控制代碼。 如果您使用預設值 **0**，則會取得標準的揮手旗標 Windows 標誌圖示。

### <a name="return-value"></a>傳回值

包含類別名稱的以 NULL 結尾字串。 您可以將這個類別名稱傳遞給 `Create` `CWnd` 或其他 CWnd 衍生類別中的成員函 **式**，以建立視窗。 此名稱是由 MFC 程式庫所產生。

> [!NOTE]
> 傳回值是靜態緩衝區的指標。 若要儲存此字串，請將它指派給 `CString` 變數。

### <a name="remarks"></a>備註

MFC 程式庫會自動為您註冊多個標準視窗類別。 如果您要註冊自己的視窗類別，請呼叫這個函式。

由 `AfxRegisterWndClass` 為類別註冊的名稱取決於參數的內容。 如果您以相同參數多次呼叫 `AfxRegisterWndClass`，它只會註冊第一次呼叫的類別。 `AfxRegisterWndClass`使用相同參數的後續呼叫會傳回已註冊的類別名稱。

如果以相同參數對多個 CWnd 衍生類別呼叫 `AfxRegisterWndClass`，除了取得每個類別的獨立視窗類別之外，每個類別還會共用相同的視窗類別。 如果使用 CS_CLASSDC 類別樣式，此共用可能會造成問題。 除了多個 CS_CLASSDC 視窗類別，您最後只會有一個 CS_CLASSDC 視窗類別。 所有使用該類別的 c + + 視窗會共用相同的 DC。 若要避免這個問題，請呼叫 [AfxRegisterClass](#afxregisterclass) 來註冊類別。

如需視窗類別註冊和函式的詳細資訊，請參閱 Technical Note [TN001：視窗類別註冊](../../mfc/tn001-window-class-registration.md) `AfxRegisterWndClass` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a> AfxSetPerUserRegistration

設定應用程式是否將登錄存取重新導向至 **HKEY_CURRENT_USER** (**HKCU**) 節點。

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*\
在TRUE 表示登錄資訊會導向至 HKCU 節點。 FALSE 表示應用程式將登錄資訊寫入預設節點。 預設節點是 **HKEY_CLASSES_ROOT** (**HKCR**) 。

### <a name="remarks"></a>備註

在 Windows Vista 之前，存取登錄的應用程式通常會使用 **HKEY_CLASSES_ROOT** 節點。 不過，在 Windows Vista 或更新版本的作業系統中，您必須以提高許可權的模式執行應用程式，才能寫入 HKCR。

此方法可讓您的應用程式讀取和寫入登錄，而不需在提高許可權的模式下執行。 其運作方式是將登錄存取從 HKCR 重新導向至 HKCU。 如需詳細資訊，請參閱 [Linker Property Pages](../../build/reference/linker-property-pages.md)。

如果您啟用登錄重新導向，則架構會將 HKCR 的存取重新導向至 **HKEY_CURRENT_USER \software\classes**。 只有 MFC 和 ATL 架構會受到重新導向的影響。

預設的執行會存取 HKCR 下的登錄。

### <a name="requirements"></a>規格需求

  **標頭** afxstat_。h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a> AfxSetResourceHandle

您可以使用此函式來設定 HINSTANCE 控制碼，以決定應用程式預設資源的載入位置。

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>參數

*hInstResource*\
載入應用程式的資源的 .EXE 或 DLL 檔的執行個體或模組控制代碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a> AfxShellManager

全域 [shell 管理員](cshellmanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>規格需求

**標頭：** afxshellmanager。h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a> AfxSocketInit

在您的覆寫中呼叫此函式 `CWinApp::InitInstance` ，以初始化 Windows 通訊端。

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>參數

*lpwsaData*\
[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構的指標。 如果 *lpwsaData* 不等於 Null，則 `WSADATA` 會透過的呼叫來填滿結構的位址 `WSAStartup` 。 此函式也可確保在 `WSACleanup` 應用程式終止之前呼叫。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

在靜態連結的 MFC 應用程式中使用次要執行緒中的 MFC 通訊端時，您必須 `AfxSocketInit` 在使用通訊端的每個執行緒中呼叫，以初始化通訊端程式庫。 根據預設， `AfxSocketInit` 只會在主要執行緒中呼叫。

### <a name="requirements"></a>規格需求

  **標頭** afxsock。h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a> AfxUserToolsManager

全域 [使用者工具管理員](cusertoolsmanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>規格需求

**標頭：** afxusertoolsmanager。h

## <a name="afxwininit"></a><a name="afxwininit"></a> AfxWinInit

這個函式是由 MFC 提供的函式在 `WinMain` [CWINAPP](../../mfc/reference/cwinapp-class.md) 初始化 GUI 架構應用程式的過程中呼叫，以初始化 MFC。

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>參數

*hInstance*\
目前正在執行之模組的控制碼。

*hPrevInstance*\
應用程式先前實例的控制碼。 若是 Win32 架構的應用程式，此參數一律為 **Null**。

*lpCmdLine*\
指向以 null 終止的字串，指定應用程式的命令列。

*nCmdShow*\
指定如何顯示 GUI 應用程式的主視窗。

### <a name="remarks"></a>備註

如果主控台應用程式不使用 MFC 提供的函式 `WinMain` ，您必須 `AfxWinInit` 直接呼叫來初始化 MFC。

如果您呼叫 `AfxWinInit` 自己，則應該宣告類別的實例 `CWinApp` 。 若為主控台應用程式，您可以選擇不要從衍生您自己的類別 `CWinApp` ，而改為直接使用的實例 `CWinApp` 。 如果您決定將應用程式的所有功能保留在您的 **主**應用程式中，這項技術會很適合。

> [!NOTE]
> 當它建立元件的啟用內容時，MFC 會使用使用者模組提供的資訊清單資源。 啟用內容可在 `AfxWinInit` 中建立。 如需詳細資訊，請參閱 [MFC 模組狀態中的啟用內容支援](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)\
[CWinApp 類別](cwinapp-class.md)\
[CCoNtextMenuManager 類別](ccontextmenumanager-class.md)\
[CWnd 類別](cwnd-class.md)\
[CFrameWndEx 類別](cframewndex-class.md)\
[CMFCToolBar 類別](cmfctoolbar-class.md)\
[CKeyboardManager 類別](ckeyboardmanager-class.md)\
[CMenuTearOffManager 類別](cmenutearoffmanager-class.md)\
[CMouseManager 類別](cmousemanager-class.md)\
[CShellManager 類別](cshellmanager-class.md)\
[CUserToolsManager 類別](cusertoolsmanager-class.md)
