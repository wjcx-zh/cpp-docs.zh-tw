---
title: 應用程式資訊和管理
description: 引用 Microsoft 基礎類庫 (MFC) 應用程式資訊和管理功能。
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372506"
---
# <a name="application-information-and-management"></a>應用程式資訊和管理

編寫應用程式時,將創建單個[CWinApp](../../mfc/reference/cwinapp-class.md)派生物件。 有時,您可能希望從`CWinApp`派生物件外部獲取有關此物件的資訊。 或者,您可能需要訪問其他全域"管理器"物件。

Microsoft 基礎類別庫提供以下全域函數,以説明您完成以下任務:

## <a name="application-information-and-management-functions"></a>應用程式資訊與管理功能

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|創建新線程。|
|[AfxContext選單管理員](#afxcontextmenumanager)|指向全域[中文選單管理員的指標](ccontextmenumanager-class.md)。|
|[AfxEndThread](#afxendthread)|終止當前線程。|
|[AfxFindResourceHandle](#afxfindresourcehandle)|遍走資源鏈,按資源 ID 和資源類型定位特定資源。 |
|[AfxFreeLibrary](#afxfreelibrary)|刪除載入的動態連結庫 (DLL) 模組的引用計數。 當引用計數達到零時,模組將取消映射。|
|[AfxGetApp](#afxgetapp)|返回指向應用程式單個`CWinApp`物件的指標。|
|[AfxGetAppName](#afxgetappname)|傳回包含應用程式名稱的字串。|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|返回表示應用程式此實例的 HINSTANCE。|
|[AfxGetMainWnd](#afxgetmainwnd)|返回指向非 OLE 應用程式的當前「主」視窗或伺服器應用程式的就地幀視窗的指標。|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|使用此函數可確定應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** (**HKCU**) 節點。|
|[AfxGetResourceHandle](#afxgetresourcehandle)|將 HINSTANCE 返回到應用程式的預設資源的來源。 用於直接存取應用程式的資源。|
|[AfxGetThread](#afxgetthread)|檢索指向當前[CWinThread](../../mfc/reference/cwinthread-class.md)物件的指標。|
|[AfxInitRichEdit](#afxinitrichedit)|初始化應用程式的版本 1.0 豐富的編輯控制項。|
|[AfxInitRichEdit2](#afxinitrichedit2)|初始化版本 2.0 和更高版本的應用程式的豐富編輯控制件。|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|判斷指定的視窗是否為擴充框架物件。|
|[AfxIsMFCToolBar](#afxismfctoolbar)|判斷指定的視窗是否為工具列物件。|
|[Afx鍵盤管理員](#afxkeyboardmanager)|指向全域[鍵盤管理員的指標](ckeyboardmanager-class.md)。|
|[AfxLoadLibrary](#afxloadlibrary)|映射 DLL 模組並傳回可用於獲取 DLL 函數位址的句柄。|
|[AfxLoad圖書館Ex](#afxloadlibraryex)|使用指定的選項對應 DLL 模組,並傳回可用於獲取 DLL 函數位址的句柄。|
|[AfxMenutearoff管理員](#afxmenutearoffmanager)|指向全域[撕掉選單管理員的指標](cmenutearoffmanager-class.md)。|
|[AfxMouse管理員](#afxmousemanager)|指向全域[滑鼠管理器](cmousemanager-class.md)的指標。|
|[AfxRegisterClass](#afxregisterclass)|在使用 MFC 的 DLL 中註冊視窗類。|
|[AfxRegisterWndClass](#afxregisterwndclass)|註冊 Windows 視窗類以補充由 MFC 自動註冊的類。|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|設置應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** (**HKCU**) 節點。|
|[AfxSetResourceHandle](#afxsetresourcehandle)|設置載入應用程式的預設資源的 HINSTANCE 句柄。|
|[AfxShell經理](#afxshellmanager)|指向全域[shell 管理員的指標](cshellmanager-class.md)。 |
|[AfxSocketInit](#afxsocketinit)|在`CWinApp::InitInstance`重寫中調用以初始化 Windows 套接字。|
|[AfxUser 工具管理員](#afxusertoolsmanager)|指向全域[使用者工具管理員的指標](cusertoolsmanager-class.md)。|
|[AfxWinInit](#afxwininit)|由 MFC`WinMain`提供的 函數調用,作為基於 GUI 的應用程式的[CWinApp](../../mfc/reference/cwinapp-class.md)初始化的一部分,以初始化 MFC。 必須直接調用使用 MFC 的主控台應用程式。|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>AfxBeginThread

調用此函數以創建新線程。

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

*普芬線程普羅克*\
指向輔助線程的控制功能。 指標不能為 NULL。 此函數必須聲明如下:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThread 類別*\
從[CWinThread](../../mfc/reference/cwinthread-class.md)的物件RUNTIME_CLASS 。

*pParam*\
要傳遞給控制函數的參數。

*n優先*\
要為線程設置的優先順序。 有關可用優先順序的完整清單和說明,請參閱 Windows SDK 中的[SetThreadPriority。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)

*nStackSize*\
指定新線程堆疊的大小(以位元組為單位)。 如果為 0,堆疊大小預設與創建線程的大小堆疊相同。

*dwCreateFlags*\
指定控制建立線程的其他標誌。 這個標誌可以包含兩個值之一:

- CREATE_SUSPENDED以1的掛起計數啟動線程。 如果要在線程開始運行之前初始化`CWinThread`物件的任何成員數據(如[m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete)或派生類的任何成員,請使用CREATE_SUSPENDED。 初始化完成後,請使用[CWinThread::resumeThread](../../mfc/reference/cwinthread-class.md#resumethread)開始線程運行。 在調用線程之前`CWinThread::ResumeThread`,線程不會執行。

- **0**創建後立即啟動線程。

*lpSecurityAttrs*\
指向指定線程的安全屬性[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))結構。 如果為 NULL,則使用與創建線程相同的安全屬性。 有關此結構的詳細資訊,請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

指標指向新創建的線程物件,如果發生故障,則指向 NULL。

### <a name="remarks"></a>備註

創建輔助線程的第`AfxBeginThread`一種形式。 第二個表單表單建立一個線程,該線程可用作使用者介面線程或輔助線程。

`AfxBeginThread`創建一個新`CWinThread`物件,調用其[CreateThread](../../mfc/reference/cwinthread-class.md#createthread)函數以開始執行線程,並返回指向線程的指標。 在整個過程中進行檢查,以確保在創建的任何部分失敗時,所有物件都正確處理。 要結束線程,請從線程內調用[AfxEndThread,](#afxendthread)或從輔助線程的控制函數返回。

應用程式必須啟用多線程;否則,此函數將失敗。 有關啟用多線程的詳細資訊,請參閱[/MD、/MT/LD(使用運行時庫)。](../../build/reference/md-mt-ld-use-run-time-library.md)

有關的詳細資訊`AfxBeginThread`,請參閱文章[「多線程:創建輔助線程](../../parallel/multithreading-creating-worker-threads.md)和[多線程:創建使用者介面線程](../../parallel/multithreading-creating-user-interface-threads.md)」。

### <a name="example"></a>範例

請參考[CSocket 的範例:附加](../../mfc/reference/csocket-class.md#attach)。

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContext選單管理員

指向全域[中文選單管理員的指標](ccontextmenumanager-class.md)。

### <a name="syntax"></a>語法

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>需求

**標題:** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread

呼叫此函數以終止當前正在執行的線程。

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>參數

*n退出代碼*\
指定線程的退出代碼。

*b 刪除*\
從記憶體中刪除線程物件。

### <a name="remarks"></a>備註

必須從線程內調用才能終止。

有關的詳細資訊`AfxEndThread`,請參閱文章[「多線程:終止線程](../../parallel/multithreading-terminating-threads.md)」。

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFind資源句柄

使用 `AfxFindResourceHandle` 查核資源鏈結並依資源 ID 和資源類型尋找特定的資源。

### <a name="syntax"></a>語法

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>參數

*lpsz名稱*\
包含資源 ID 之字串的指標。
*lpsz 類型*\
資源類型的指標。 有關資源型態的清單,請參閱在 Windows SDK 中[尋找資源](/windows/win32/api/winbase/nf-winbase-findresourcea)。

### <a name="return-value"></a>傳回值

包含資源之模組的控制代碼。

### <a name="remarks"></a>備註

`AfxFindResourceHandle`查找特定資源,並將句柄返回到包含資源的模組。 資源可能位於載入的任何 MFC 擴展 DLL 中。 `AfxFindResourceHandle` 會告知您哪一個 DLL 中內含資源。

模組會依此順序搜尋：

1. 主模組(如果是 MFC 擴展 DLL)。

1. 非系統模組。

1. 特定語言的模組。

1. 主模組,如果是系統 DLL。

1. 系統模組。

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>Afx自由圖書館

`AfxFreeLibrary` 和 `AfxLoadLibrary` 會保留每個載入的程式庫模組的參考計數。

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>參數

*hInstLib*\
所載入程式庫模組的控制代碼。 [AfxLoad庫](#afxloadlibrary)返回此句柄。

### <a name="return-value"></a>傳回值

如果函式成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`AfxFreeLibrary` 會將載入的動態連結程式庫 (DLL) 模組的參考計數遞減。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。 每次呼叫 `AfxLoadLibrary` 時，此參考計數會遞增。

在取消對應程式庫模組之前，系統會啟用 DLL 來中斷處理序使用它的連結。 這樣做使 DLL 有機會清理為當前進程分配的資源。 在進入點函式傳回之後，程式庫模組就會從目前處理序的位址空間中移除。

使用 `AfxLoadLibrary` 對應 DLL 模組。

如果應用程式使用多個`AfxFreeLibrary`線`AfxLoadLibrary`程 ,請確保使用和`FreeLibrary``LoadLibrary`(而不是 Win32 函數和)。 使用`AfxLoadLibrary``AfxFreeLibrary`並確保在載入和卸載 MFC 擴展 DLL 時執行的啟動和關閉代碼不會損壞全域 MFC 狀態。

### <a name="example"></a>範例

請參閱[AfxLoadLibrary](#afxloadlibrary)的示例。

### <a name="requirements"></a>需求

  **標題**afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>AfxGetApp

此函數返回的指標可用於訪問應用程式資訊,如主消息調度代碼或最上面的視窗。

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>傳回值

指向應用程式的單個`CWinApp`物件的指標。

### <a name="remarks"></a>備註

如果此方法返回 NULL,則可能表示應用程式主視窗尚未完全初始化。 它還可能表示存在問題。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>AfxGetApp名稱

返回的字串可用於診斷消息,或用作臨時字串名稱的根。

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>傳回值

包含應用程式名稱的 NULL 結尾字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetinstanceHandle

這個函式可讓您擷取目前應用程式的執行個體控制代碼。

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>傳回值

應用程式的當前實例的 HINSTANCE。 如果從與 MFC USRDLL 版本連結的 DLL 內調用,則返回 DLL 的 HINSTANCE。

### <a name="remarks"></a>備註

`AfxGetInstanceHandle`始終返回可執行檔的 HINSTANCE (。EXE),除非是從與 MFC USRDLL 版本連結的 DLL 內調用的。 在這種情況下,它將 HINSTANCE 返回 DLL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>阿FXGetMainwnd

如果應用程式是 OLE 伺服器,請呼叫此函式以檢索指向應用程式活動主視窗的指標。 使用此結果,而不是直接引用應用程式物件的[m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd)成員。

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>傳回值

如果伺服器具有在活動容器內處於活動狀態的物件,則返回指向包含就地活動文檔的框架視窗物件的指標。

如果容器內沒有就地處於活動狀態的物件,或者應用程式不是 OLE 伺服器,則此函數將返回應用程式物件的*m_pMainWnd。*

如果從應用程式的主執行緒呼叫 `AfxGetMainWnd`，則它會根據上述規則傳回應用程式的主視窗。 如果從應用程式的次要執行緒呼叫函式時，則函式會傳回與發出呼叫的執行緒關聯的主視窗。

### <a name="remarks"></a>備註

如果應用程式不是 OLE 伺服器,則呼叫此函數等效於直接引用應用程式物件的*m_pMainWnd*成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>AfxGetPer用戶註冊

使用此函數可確定應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** (**HKCU**) 節點。

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>傳回值

TRUE 表示註冊表資訊定向到 HKCU 節點。 FALSE 指示應用程式將註冊表資訊寫入預設節點。 默認節點為**HKEY_CLASSES_ROOT** **(HKCR**)。

### <a name="remarks"></a>備註

開啟註冊表重定向,框架會將存取從**HKCR**重定向到**HKEY_CURRENT_USER_軟體\類別**。 只有 MFC 和 ATL 框架受重定向的影響。

要更改應用程式是否重定向註冊表存取,請使用[AfxSetPerUser 註冊](#afxsetperuserregistration)。

### <a name="requirements"></a>需求

  **標題**afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGet資源手柄

使用此函數返回的 HEXAMPLE 句柄直接存取應用程式的資源,例如,在調用`FindResource`Windows 函數 中。

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>傳回值

載入應用程式的預設資源的 HINSTANCE 句柄。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread

呼叫此函數以獲取指向表示當前正在執行的線程的[CWinThread](../../mfc/reference/cwinthread-class.md)物件的指標。

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>傳回值

目前執行中之執行緒的指標；否則為 NULL。

### <a name="remarks"></a>備註

必須從線程內調用。

> [!NOTE]
> 如果要移植從 Visual C++ 版本`AfxGetThread`4.2、5.0 或`AfxGetThread`6.0 調用的 MFC 專案,則如果找不到線程,則調用[AfxGetApp。](#afxgetapp) 在編譯器的較新版本中,如果未`AfxGetThread`找到線程,則返回 NULL。 如果您要應用程式執行緒，則必須呼叫 `AfxGetApp`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>阿FXInitrichedit

調用此函數以初始化應用程式的富編輯控制件(版本1.0)。

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>備註

此功能用於向後相容性。 新的應用程序應該使用[AfxInitrichedit2。](#afxinitrichedit2)

`AfxInitRichEdit`負載 RICHED32。DLL 用於初始化富編輯控制項的版本1.0。 要使用富編輯控制件的 2.0 版和 3.0 版本,RICHED20。需要載入 DLL。 它載入透過調用[AfxInitRichEdit2。](#afxinitrichedit2)

要將現有 VisualC++ 應用程式中的豐富編輯控制檔更新到版本 2.0,請開啟 。RC 檔案作為文本,將每個富編輯控制件的類名稱從"RICHEDIT"更改為"RichEdit20a"。 然後將 呼`AfxInitRichEdit`叫取代`AfxInitRichEdit2`為 。

如果尚未為進程初始化庫,則此函數還會初始化公共控件庫。 如果直接從 MFC 應用程式使用豐富的編輯控制項,請呼叫此函數以確保 MFC 已正確初始化豐富的編輯控制執行時。 如果您調用`Create`[CRichEditCtrl、CRichEditView](../../mfc/reference/cricheditctrl-class.md)或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的方法,您通常不需要呼叫此函數,但在某些情況下可能有必要呼叫[CRichEditView](../../mfc/reference/cricheditview-class.md)此函數。

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>阿FXInitrichedit2

呼叫此函式以初始化應用程式的 Rich Edit 控制項 (2.0 版和更新版本)。

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>備註

呼叫此函式以載入 RICHED20.DLL 和初始化 2.0 版的 Rich Edit 控制項。 如果您調用`Create`[CRichEditCtrl、CRichEditView](../../mfc/reference/cricheditctrl-class.md)或[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的方法,您通常不需要呼叫此函數,但在某些情況下可能有必要呼叫[CRichEditView](../../mfc/reference/cricheditview-class.md)此函數。

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>AfxIs 擴充框架類

判斷指定的視窗是否為擴充框架物件。

### <a name="syntax"></a>語法

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>參數

*pwnd*\
[在]指向派生自`CWnd`的物件的指標。

### <a name="return-value"></a>傳回值

如果提供的視窗是擴展幀物件,則為 TRUE;如果提供的視窗是擴展幀物件,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

如果*pWnd*派生自以下類之一,則此方法返回 TRUE:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

當您必須驗證函式或方法參數是否為擴充框架物件時，此方法很有用。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>AfxIsMFCToolbar

判斷指定的視窗是否為工具列物件。

### <a name="syntax"></a>語法

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*\
[在]指向派生自`CWnd`的物件的指標。

### <a name="return-value"></a>傳回值

如果提供的視窗是工具列物件,則為 TRUE;如果提供的視窗是工具列物件,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

如果*pWnd*派`CMFCToolBar`生自 ,則此`TRUE`方法將返回 。 當您必須驗證函式或方法參數是否為 `CMFCToolBar` 物件時，這個方法就很有用。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>Afx鍵盤管理員

指向全域[鍵盤管理員的指標](ckeyboardmanager-class.md)。

### <a name="syntax"></a>語法

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>需求

**標題:** afx鍵盤管理員.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>AfxLoad庫

使用 `AfxLoadLibrary` 對應 DLL 模組。

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>參數

*lpszModule 名稱*\
包含模組名稱的 null 連接端字串(或 。DLL 或 。EXE 檔)。 指定的名稱是模組的檔名。

如果字串指定路徑,但檔在指定的目錄中不存在,則函數將失敗。

如果未指定路徑,並且省略了檔案名副檔名,則預設副檔名 。DLL 被追加。 但是,檔名字串可以包含尾隨點字元 (.), 以指示模組名稱沒有擴展名。 當未指定路徑時,此函數會使用[桌面應用程式的搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

### <a name="return-value"></a>傳回值

如果函數成功,返回值是模組的句柄。 發生故障時,返回值為 NULL。

### <a name="remarks"></a>備註

它返回可在[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)中使用的句柄來獲取 DLL 函數的位址。 `AfxLoadLibrary`還可用於映射其他可執行模組。

每個進程維護每個載入的庫模組的引用計數。 每次`AfxLoadLibrary`調用時都會增加此引用計數,並且`AfxFreeLibrary`每次 調用時都會遞減。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。

如果應用程式使用多個`AfxLoadLibrary`線`AfxFreeLibrary`程 ,並且它動態載入`LoadLibrary``FreeLibrary`MFC 擴展 DLL,請確保使用 (而不是 Win32 函數和)。 使用`AfxLoadLibrary`並`AfxFreeLibrary`確保 在載入和卸載 MFC 擴展 DLL 時執行的啟動和關閉代碼不會損壞全域 MFC 狀態。

在`AfxLoadLibrary`應用程式中使用需要您動態連結到 MFC 的 DLL 版本。 僅當 MFC`AfxLoadLibrary`以 DLL 身份連結到應用程式時,才會包含的標頭檔。Afxdll_.h。 此要求是設計原因,因為您必須連結到 MFC 的 DLL 版本才能使用或創建 MFC 擴展 DLL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>需求

  **標題**afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoad圖書館Ex

使用 `AfxLoadLibraryEx` 對應 DLL 模組。

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>參數

*lpFile 名稱*\
包含模組名稱的 null 連接端字串(或 。DLL 或 。EXE 檔)。 指定的名稱是模組的檔名。

如果字串指定路徑,但檔在指定的目錄中不存在,則函數將失敗。

如果未指定路徑,並且省略了檔案名副檔名,則預設副檔名 。DLL 被追加。 但是,檔名字串可以包含尾隨點字元 (.), 以指示模組名稱沒有擴展名。 當未指定路徑時,此函數會使用[桌面應用程式的搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)。

*hFile*\
這個參數保留給未來使用。 它必須為 NULL。

*dwFlags*\
載入模組時要執行的操作。 如果未指定標誌,則此函數的行為與`AfxLoadLibrary`函數相同。 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)文檔中介紹了此參數的可能值。

### <a name="return-value"></a>傳回值

如果函數成功,返回值是模組的句柄。 發生故障時,返回值為 NULL。

### <a name="remarks"></a>備註

`AfxLoadLibraryEx`返回可在[GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)中使用的句柄來獲取 DLL 函數的位址。 `AfxLoadLibraryEx`還可用於映射其他可執行模組。

每個進程維護每個載入的庫模組的引用計數。 每次`AfxLoadLibraryEx`調用時都會增加此引用計數,並且`AfxFreeLibrary`每次 調用時都會遞減。 在參考計數達到零時，模組就從呼叫處理序的位址空間取消對應，且控制代碼不再有效。

如果應用程式使用多個`AfxLoadLibraryEx`線`AfxFreeLibrary`程 ,並且它動態載入`LoadLibraryEx``FreeLibrary`MFC 擴展 DLL,請確保使用 (而不是 Win32 函數和)。 使用`AfxLoadLibraryEx``AfxFreeLibrary`並確保在載入和卸載 MFC 擴展 DLL 時執行的啟動和關閉代碼不會損壞全域 MFC 狀態。

在`AfxLoadLibraryEx`應用程式中使用需要您動態連結到 MFC 的 DLL 版本。 僅當 MFC`AfxLoadLibraryEx`以 DLL 身份連結到應用程式時,才會包含的標頭檔。Afxdll_.h。 此要求是設計原因,因為您必須連結到 MFC 的 DLL 版本才能使用或創建 MFC 擴展 DLL。

### <a name="requirements"></a>需求

  **標題**afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenutearoff管理員

指向全域[撕掉選單管理員的指標](cmenutearoffmanager-class.md)。

### <a name="syntax"></a>語法

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>需求

**標題:** afxmenutearoff 管理員.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouse管理員

指向全域[滑鼠管理器](cmousemanager-class.md)的指標。

### <a name="syntax"></a>語法

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>需求

**標題:** afxmouse 管理器.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>Afx註冊類

使用這個函式在使用 MFC 的 DLL 中登錄視窗類別。

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>參數

*lpWndClass*\
指向[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構的指標,其中包含有關要註冊的視窗類的資訊。 有關此結構的詳細資訊,請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

如果類別成功登錄為 TRUE；否則為 FALSE。

### <a name="remarks"></a>備註

如果您使用這個函式，類別會在卸載 DLL 時自動解除登錄。

在非 DLL`AfxRegisterClass`生成中 ,識別符定義為映射到`RegisterClass`Windows 函數 的宏,因為在應用程式中註冊的類將自動取消註冊。 如果使用`AfxRegisterClass``RegisterClass`而不是 ,則可以在應用程式和 DLL 中不使用更改即可使用代碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>Afx註冊WndClass

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
為視窗類指定使用位-OR** (&#124;**) 運算符創建的 Windows 類樣式或樣式組合。 有關類樣式的清單,請參閱 Windows SDK 中的[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構。 如果 NULL,則預設值設定如下:

- 當使用者按兩下滑鼠時，會將按兩下訊息傳送至視窗程序，將滑鼠樣式設定 CS_DBLCLKS。

- 將箭號游標樣式設定為 Windows 標準 IDC_ARROW。

- 將背景筆設定為 NULL,因此視窗不會擦除其背景。

- 將圖示設定為標準的旗標 Windows 標誌圖示。

*h游標*\
指定將在從視窗類別建立之各個視窗中安裝的游標資源控制代碼。 如果使用預設值**0**,您將獲得標準IDC_ARROW游標。

*hbr背景*\
指定將在從視窗類別建立之各個視窗中安裝的筆刷資源控制代碼。 如果使用預設值**0**,則具有 NULL 背景筆,預設情況下,視窗在處理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)時不會擦除其背景。

*hIcon*\
指定將在從視窗類別建立之各個視窗中安裝的圖示資源控制代碼。 如果使用預設值**0**,您將獲得標準的"揮舞"標誌 Windows 徽標圖示。

### <a name="return-value"></a>傳回值

包含類別名稱的以 NULL 結尾字串。 您可以將此類名稱傳遞給`Create``CWnd`中的成員函數或其他**CWnd 派生**類以創建視窗。 此名稱是由 MFC 程式庫所產生。

> [!NOTE]
> 傳回值是靜態緩衝區的指標。 若要儲存此字串，請將它指派給 `CString` 變數。

### <a name="remarks"></a>備註

MFC 程式庫會自動為您註冊多個標準視窗類別。 如果您要註冊自己的視窗類別，請呼叫這個函式。

由 `AfxRegisterWndClass` 為類別註冊的名稱取決於參數的內容。 如果您以相同參數多次呼叫 `AfxRegisterWndClass`，它只會註冊第一次呼叫的類別。 稍後調用`AfxRegisterWndClass`具有相同參數的調用將返回已註冊的類名。

如果以相同參數對多個 CWnd 衍生類別呼叫 `AfxRegisterWndClass`，除了取得每個類別的獨立視窗類別之外，每個類別還會共用相同的視窗類別。 如果使用CS_CLASSDC類樣式,則此共用可能會導致問題。 您最終只能使用一個視窗類CS_CLASSDC而不是多個CS_CLASSDC視窗類。 使用該類的所有C++視窗共用同一個 DC。 為了避免此問題,請致電[AfxRegisterClass](#afxregisterclass)註冊該類。

請參閱技術說明[TN001:視窗類註冊](../../mfc/tn001-window-class-registration.md),瞭解有關視窗類`AfxRegisterWndClass`註冊和 功能的詳細資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>AfxSetPer用戶註冊

設置應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** (**HKCU**) 節點。

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>參數

*b 啟用*\
[在]TRUE 表示註冊表資訊定向到 HKCU 節點。 FALSE 指示應用程式將註冊表資訊寫入預設節點。 默認節點為**HKEY_CLASSES_ROOT** **(HKCR**)。

### <a name="remarks"></a>備註

在 Windows Vista 之前,訪問註冊表的應用程式通常使用**HKEY_CLASSES_ROOT**節點。 但是,使用 Windows Vista 或更高版本的作業系統,您必須以提升模式執行應用程式才能寫入 HKCR。

此方法使應用程式能夠讀取和寫入註冊表,而無需在提升模式下運行。 它的工作原理是將註冊處的註冊存取從香港註冊處轉往香港聯大。 如需詳細資訊，請參閱 [Linker Property Pages](../../build/reference/linker-property-pages.md)。

開啟註冊表重定向,框架會將存取從 HKCR 重定到**HKEY_CURRENT_USER_軟體\類別**。 只有 MFC 和 ATL 框架受重定向的影響。

預設實現訪問 HKCR 下的註冊表。

### <a name="requirements"></a>需求

  **標題**afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSet資源句柄

使用此函數可以設置 HINSTANCE 句柄,確定應用程式的預設資源載入位置。

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>參數

*hInst 資源*\
載入應用程式的資源的 .EXE 或 DLL 檔的執行個體或模組控制代碼。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShell經理

指向全域[shell 管理員的指標](cshellmanager-class.md)。

### <a name="syntax"></a>語法

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>需求

**標題:** afxshell管理員.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>阿FXSocketinit

在`CWinApp::InitInstance`重寫中調用此函數以初始化 Windows 套接字。

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>參數

*lpwsaData*\
指向[WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata)結構的指標。 如果*lpwsaData*不等於 NULL,則`WSADATA`結構的位址將`WSAStartup`由呼叫填充。 此函數還可確保`WSACleanup`在應用程式終止之前為您調用。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

在靜態連結的 MFC 應用程式中的輔助線程中使用 MFC`AfxSocketInit`套接字時,必須呼叫使用 socket 初始化套接字型檔的每個線程。 預設情況下,`AfxSocketInit`僅在主線程中呼叫。

### <a name="requirements"></a>需求

  **頭**afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUser 工具管理員

指向全域[使用者工具管理員的指標](cusertoolsmanager-class.md)。

### <a name="syntax"></a>語法

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>需求

**標題:** afxuser工具管理員.h

## <a name="afxwininit"></a><a name="afxwininit"></a>阿FXWininit

此函數由 MFC`WinMain`提供的 函數調用,作為基於 GUI 的應用程式的[CWinApp](../../mfc/reference/cwinapp-class.md)初始化的一部分,以初始化 MFC。

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>參數

*h實例*\
當前正在運行的模組的句柄。

*hPrev 實體*\
應用程式前一個實例的句柄。 對於基於 Win32 的應用程式,此參數始終為**NULL**。

*lpCmdline*\
指定應用程式指令列的 null 連接字串。

*nCmdShow*\
指定如何顯示 GUI 應用程式的主視窗。

### <a name="remarks"></a>備註

對於不使用 MFC`WinMain`提供的 函數的主控台應用程式,`AfxWinInit`必須直接調用 以初始化 MFC。

如果您稱自己為類`AfxWinInit`,則應`CWinApp`聲明 類的實例。 對於控制台應用程式,您可以選擇不派生`CWinApp`自己的類,而是直接使用 實`CWinApp`例。 如果您決定在**main**的實現中保留應用程式的所有功能,則此技術是合適的。

> [!NOTE]
> 為程式集創建啟動上下文時,MFC 將使用使用者模組提供的清單資源。 啟用內容可在 `AfxWinInit` 中建立。 有關詳細資訊,請參閱[MFC 模組狀態中對啟動上下文的支援](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)\
[CWinApp 類別](cwinapp-class.md)\
[CContextMenuManager 類別](ccontextmenumanager-class.md)\
[CWnd 類別](cwnd-class.md)\
[CFramewndEx 類別](cframewndex-class.md)\
[CMFCToolBar 類別](cmfctoolbar-class.md)\
[鍵盤管理員類別](ckeyboardmanager-class.md)\
[CMenuTearoff 經理類](cmenutearoffmanager-class.md)\
[滑鼠管理員類別](cmousemanager-class.md)\
[CShellManager 類別](cshellmanager-class.md)\
[CUserToolsManager 類別](cusertoolsmanager-class.md)
