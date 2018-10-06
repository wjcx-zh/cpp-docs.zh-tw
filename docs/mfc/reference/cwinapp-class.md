---
title: CWinApp 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
dev_langs:
- C++
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86adc1e2337b32ced77cafda92229ed9724ba548
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821513"
---
# <a name="cwinapp-class"></a>CWinApp 類別

Windows 應用程式物件所衍生自的基底類別。

## <a name="syntax"></a>語法

```
class CWinApp : public CWinThread
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinApp::CWinApp](#cwinapp)|建構 `CWinApp` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinApp::AddDocTemplate](#adddoctemplate)|將應用程式的可用文件範本清單中的文件範本。|
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|將最近使用過的 (MRU) 檔案清單中的檔案名稱。|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|非預期地結束應用程式時由架構呼叫。|
|[CWinApp::CloseAllDocuments](#closealldocuments)|關閉所有開啟的文件。|
|[CWinApp::CreatePrinterDC](#createprinterdc)|建立印表機裝置內容。|
|[CWinApp::DelRegTree](#delregtree)|刪除指定的索引鍵和其所有子機碼。|
|[CWinApp::DoMessageBox](#domessagebox)|Implements [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)應用程式。|
|[CWinApp::DoWaitCursor](#dowaitcursor)|將等待游標，開啟和關閉。|
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|可讓應用程式 D2D 支援。 初始化主視窗之前先呼叫這個方法。|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|實作 HTMLHelp 應用程式，而不是 WinHelp。|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|可讓工作列互動。|
|[CWinApp::ExitInstance](#exitinstance)|覆寫您的應用程式終止時清除。|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|擷取應用程式的復原方法的輸入的參數。|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|傳回重新啟動管理員會等到復原回撥函式傳回的時間的長度。|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|重新啟動管理員傳回的旗標。|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|傳回機碼 hkey_current_user\\\RegistryKey\ProfileName 「 軟體 」。|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|取得應用程式的這個執行個體中的資料復原處理常式。|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|擷取第一個文件範本的位置。|
|[CWinApp::GetHelpMode](#gethelpmode)|擷取說明應用程式所使用的型別。|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|擷取的文件範本的位置。 可以使用的遞迴。|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|擷取印表機裝置的預設值。|
|[CWinApp::GetProfileBinary](#getprofilebinary)|從應用程式中的項目擷取二進位資料。INI 檔案。|
|[CWinApp::GetProfileInt](#getprofileint)|擷取應用程式中的項目中的整數。INI 檔案。|
|[CWinApp::GetProfileString](#getprofilestring)|從應用程式的項目擷取的字串。INI 檔案。|
|[CWinApp::GetSectionKey](#getsectionkey)|傳回機碼 hkey_current_user\\\RegistryKey\AppName\lpszSection 「 軟體 」。|
|[CWinApp::HideApplication](#hideapplication)|隱藏應用程式前關閉所有文件。|
|[CWinApp::HtmlHelp](#htmlhelp)|呼叫`HTMLHelp`Windows 函式。|
|[Cwinapp:: Initinstance](#initinstance)|覆寫以執行 Windows 的執行個體初始化，例如建立視窗物件。|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|會告知是否已啟用 Windows 7 工作列互動。|
|[CWinApp::LoadCursor](#loadcursor)|載入資料指標的資源。|
|[CWinApp::LoadIcon](#loadicon)|載入圖示資源。|
|[CWinApp::LoadOEMCursor](#loadoemcursor)|載入 Windows OEM 預先定義的資料指標， **OCR_** 常數會指定在 WINDOWS 中。H.|
|[CWinApp::LoadOEMIcon](#loadoemicon)|載入 Windows OEM 預先定義的圖示， **OIC_** 常數會指定在 WINDOWS 中。H.|
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|載入 Windows 預先定義的資料指標， **IDC_** 常數會指定在 WINDOWS 中。H.|
|[CWinApp::LoadStandardIcon](#loadstandardicon)|載入 Windows 預先定義的圖示， **IDI_** 常數會指定在 WINDOWS 中。H.|
|[CWinApp::OnDDECommand](#onddecommand)|呼叫的架構，以回應動態資料交換 (DDE) 執行命令。|
|[CWinApp::OnIdle](#onidle)|覆寫以執行應用程式專屬的閒置時間處理。|
|[CWinApp::OpenDocumentFile](#opendocumentfile)|由架構呼叫以從檔案開啟的文件。|
|[CWinApp::ParseCommandLine](#parsecommandline)|剖析出個別的參數和命令列中的旗標。|
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|篩選訊息，再將它們分派至 Windows 函式[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)。|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|到達應用程式之前，會攔截特定訊息。|
|[CWinApp::ProcessShellCommand](#processshellcommand)|處理命令列引數和旗標。|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|攔截所有的應用程式的訊息和命令處理常式所擲回未處理例外狀況。|
|[CWinApp::Register](#register)|執行自訂的註冊。|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|重新啟動管理員會向應用程式。|
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|決定是否重新啟動管理員會重新開啟應用程式意外結束時所開啟的檔案。|
|[CWinApp::RestartInstance](#restartinstance)|處理重新啟動管理員啟動應用程式重新啟動。|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|決定是否重新啟動管理員會將檔案還原重新啟動應用程式時。|
|[Cwinapp:: Run](#run)|會執行預設訊息迴圈。 覆寫以自訂訊息迴圈。|
|[CWinApp::RunAutomated](#runautomated)|測試應用程式的命令列 **/Automation**選項。 已過時。 相反地，使用中的值[CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated)之後呼叫[ParseCommandLine](#parsecommandline)。|
|[CWinApp::RunEmbedded](#runembedded)|測試應用程式的命令列 **/內嵌**選項。 已過時。 相反地，使用中的值[CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded)之後呼叫[ParseCommandLine](#parsecommandline)。|
|[CWinApp::SaveAllModified](#saveallmodified)|會提示使用者儲存所有已修改的文件。|
|[CWinApp::SelectPrinter](#selectprinter)|選取先前的使用者，透過列印對話方塊，指出印表機。|
|[CWinApp::SetHelpMode](#sethelpmode)|設定及初始化說明應用程式所使用的類型。|
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|決定是否重新啟動管理員復原意外結束的應用程式。|
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|決定是否重新啟動管理員時，自動儲存開啟的文件以固定間隔。|
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|決定是否重新啟動管理員時，自動儲存任何開啟的文件時重新啟動應用程式。|
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|判斷應用程式是否支援重新啟動管理員。|
|[CWinApp::Unregister](#unregister)|取消註冊已知由註冊的所有項目`CWinApp`物件。|
|[CWinApp::WinHelp](#winhelp)|呼叫`WinHelp`Windows 函式。|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|寫入二進位資料的應用程式中的項目。INI 檔案。|
|[Cwinapp:: Writeprofileint](#writeprofileint)|將整數寫入至應用程式的項目。INI 檔案。|
|[CWinApp::WriteProfileString](#writeprofilestring)|將字串寫入應用程式中的項目。INI 檔案。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|可讓使用者從 Windows 檔案管理員中開啟資料檔案。|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|載入標準。INI 檔案設定並啟用到最近的檔案清單功能。|
|[CWinApp::OnContextHelp](#oncontexthelp)|處理應用程式內的 SHIFT + F1 說明。|
|[CWinApp::OnFileNew](#onfilenew)|會實作 ID_FILE_NEW 命令。|
|[CWinApp::OnFileOpen](#onfileopen)|會實作 ID_FILE_OPEN 命令。|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|會實作 ID_FILE_PRINT_SETUP 命令。|
|[CWinApp::OnHelp](#onhelp)|在應用程式 (使用目前的內容) 中處理 F1 說明。|
|[CWinApp::OnHelpFinder](#onhelpfinder)|處理 ID_HELP_FINDER 和 ID_DEFAULT_HELP 命令。|
|[CWinApp::OnHelpIndex](#onhelpindex)|處理 ID_HELP_INDEX 命令，並提供預設的說明主題。|
|[CWinApp::OnHelpUsing](#onhelpusing)|處理 ID_HELP_USING 命令。|
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|使用 Windows 檔案管理員中註冊應用程式的所有文件類型。|
|[CWinApp::SetAppID](#setappid)|明確地設定應用程式的應用程式使用者模型識別碼。 任何使用者介面會呈現給使用者 （的最佳位置是應用程式建構函式） 之前，應該呼叫這個方法。|
|[CWinApp::SetRegistryKey](#setregistrykey)|會儲存在登錄中，而不是應用程式設定。INI 檔案。|
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|取消註冊應用程式的所有文件類型與 Windows 檔案管理員。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|指出使用者是否為 （通常使用叫用 SHIFT + F1） 的說明內容模式。|
|[CWinApp::m_eHelpType](#m_ehelptype)|指定應用程式所使用的說明的類型。|
|[CWinApp::m_hInstance](#m_hinstance)|識別應用程式的目前執行個體。|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|指向以 null 終止的字串，指定命令列應用程式。|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|指定一開始要顯示的視窗的方式。|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|OLE 伺服器時就地啟用作用中的容器應用程式的主視窗的指標。|
|[CWinApp::m_pszAppID](#m_pszappid)|應用程式使用者模型識別碼。|
|[CWinApp::m_pszAppName](#m_pszappname)|指定應用程式的名稱。|
|[CWinApp::m_pszExeName](#m_pszexename)|應用程式的模組名稱。|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|應用程式的說明檔案的路徑。|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|應用程式。INI 檔案名稱。|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|用來判斷儲存應用程式設定檔設定的完整的登錄機碼。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|決定重新啟動管理員的運作方式的旗標。|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|以毫秒為單位時，自動儲存之間的時間長度。|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|應用程式的資料復原處理常式的指標。|

## <a name="remarks"></a>備註

應用程式物件會提供成員函式，來初始化您的應用程式 （和它的每個執行個體），以及在執行應用程式。

使用 Microsoft Foundation classes 的每個應用程式只能包含一個物件衍生自`CWinApp`。 此物件建構其他 c + + 的全域物件時所建構，並已可使用，當呼叫 Windows`WinMain`函式，這由 Microsoft Foundation Class Library 所提供。 宣告您的衍生`CWinApp`全域層級的物件。

當您衍生的應用程式類別，從`CWinApp`，覆寫[InitInstance](#initinstance)成員函式來建立您的應用程式主視窗物件。

除了`CWinApp`成員函式，Mfc 程式庫提供下列全域的函式，以存取您`CWinApp`物件和其他通用資訊：

- [AfxGetApp](application-information-and-management.md#afxgetapp)取得的指標`CWinApp`物件。

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)取得目前的應用程式執行個體的控制代碼。

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle)取得應用程式的資源的控制代碼。

- [AfxGetAppName](application-information-and-management.md#afxgetappname)取得字串，包含應用程式的名稱的指標。 或者，如果您有一個指向`CWinApp`物件，請使用`m_pszExeName`取得應用程式的名稱。

請參閱[CWinApp： 應用程式類別](../../mfc/cwinapp-the-application-class.md)如需詳細資訊`CWinApp`類別，包括下列概觀：

- `CWinApp`-衍生應用程式精靈所撰寫的程式碼。

- `CWinApp`執行順序，您的應用程式中的角色。

- `CWinApp`預設成員函式實作。

- `CWinApp`索引鍵可覆寫。

`m_hPrevInstance`資料成員不存在。 如需偵測的上一個例`CWinApp`，請參閱知識庫文件 「 如何識別前一個執行個體的應用程式 」 (KB106385)，網址[ http://support.microsoft.com/default.aspxscid=kb; 106385](http://support.microsoft.com/default.aspxscid=kb;106385)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="adddoctemplate"></a>  CWinApp::AddDocTemplate

呼叫此成員函式，將文件範本新增至應用程式所維護的可用文件範本的清單。

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>參數

*pTemplate*<br/>
指標`CDocTemplate`新增。

### <a name="remarks"></a>備註

您應該將所有文件至應用程式的範本，然後再呼叫[RegisterShellFileTypes](#registershellfiletypes)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="addtorecentfilelist"></a>  CWinApp::AddToRecentFileList

呼叫此成員函式，以新增*lpszPathName*到 MRU 的檔案清單。

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>參數

*lpszPathName*<br/>
檔案的路徑。

### <a name="remarks"></a>備註

您應該呼叫[LoadStdProfileSettings](#loadstdprofilesettings)成員函式來載入目前的 MRU 檔案清單，才能使用此成員函式。

開啟檔案或執行另存新檔命令以使用新名稱儲存檔案時，架構會呼叫此成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="applicationrecoverycallback"></a>  CWinApp::ApplicationRecoveryCallback

非預期地結束應用程式時由架構呼叫。

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>參數

*lpvParam*<br/>
[in]保留供日後使用。

### <a name="return-value"></a>傳回值

如果這個方法成功，，0如果發生錯誤時，非零值。

### <a name="remarks"></a>備註

如果您的應用程式支援重新啟動管理員，架構會呼叫此函式，當您的應用程式意外結束。

預設實作`ApplicationRecoveryCallback`使用`CDataRecoveryHandler`登錄中儲存目前開啟的文件清單。 這個方法就不自動儲存任何檔案。

若要自訂行為，請覆寫中衍生此函式[CWinApp 類別](../../mfc/reference/cwinapp-class.md)，或做為參數傳遞您自己的應用程式的復原方法[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。

##  <a name="closealldocuments"></a>  CWinApp::CloseAllDocuments

呼叫此成員函式來結束前，請關閉所有開啟的文件。

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>參數

*bEndSession*<br/>
指定要結束 Windows 工作階段。 它會為 TRUE，如果工作階段正在結束;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫[HideApplication](#hideapplication)再呼叫`CloseAllDocuments`。

##  <a name="createprinterdc"></a>  CWinApp::CreatePrinterDC

呼叫此成員函式，來建立從所選印表機的印表機裝置內容 (DC)。

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>參數

*dc*<br/>
印表機裝置內容的參考。

### <a name="return-value"></a>傳回值

如果印表機裝置內容成功; 建立，非零值。否則為 0。

### <a name="remarks"></a>備註

`CreatePrinterDC` 初始化您在傳址方式傳遞，因此您可以使用它來列印裝置內容。

如果函式成功，當您完成列印時，您必須銷毀的裝置內容。 您可以讓的解構函式[CDC](../../mfc/reference/cdc-class.md)物件會執行它，或者，您可以明確地呼叫[CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc)。

##  <a name="cwinapp"></a>  CWinApp::CWinApp

建構`CWinApp`物件並傳遞*lpszAppName*儲存為應用程式名稱。

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>參數

*lpszAppName*<br/>
以 null 結尾的字串，其中包含 Windows 所使用的應用程式名稱。 如果未提供這個引數，或為 NULL，`CWinApp`使用資源字串 AFX_IDS_APP_TITLE 或可執行檔的檔名。

### <a name="remarks"></a>備註

您應該建構一個全域物件您`CWinApp`-衍生的類別。 您只能有一個`CWinApp`應用程式中的物件。 建構函式儲存的指標`CWinApp`物件，讓`WinMain`可以呼叫物件的成員函式來初始化和執行應用程式。

##  <a name="delregtree"></a>  CWinApp::DelRegTree

刪除特定的登錄機碼和所有子機碼。

```
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName);

LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hParentKey*<br/>
登錄機碼的控制代碼。

*strKeyName*<br/>
要刪除的登錄機碼名稱。

*pTM*<br/>
CAtlTransactionManager 物件的指標。

### <a name="return-value"></a>傳回值

如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。

### <a name="remarks"></a>備註

呼叫此函式來刪除指定的機碼和其子機碼。

##  <a name="domessagebox"></a>  CWinApp::DoMessageBox

架構會呼叫此成員函式，來實作全域函式的訊息方塊[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)。

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>參數

*lpszPrompt*<br/>
在訊息方塊文字的位址。

*n*<br/>
訊息方塊[樣式](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)。

*nIDPrompt*<br/>
說明內容字串索引。

### <a name="return-value"></a>傳回值

會傳回相同的值`AfxMessageBox`。

### <a name="remarks"></a>備註

請勿呼叫此成員函式，以開啟訊息方塊;使用`AfxMessageBox`改。

若要自訂您整個應用程式處理此成員函式會覆寫`AfxMessageBox`呼叫。

##  <a name="dowaitcursor"></a>  CWinApp::DoWaitCursor

若要實作的架構會呼叫此成員函式[CWaitCursor](../../mfc/reference/cwaitcursor-class.md)， [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，和[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>參數

*則 nCode*<br/>
如果這個參數是 1，則會顯示等待游標。 如果為 0，將等待游標會還原不遞增參考計數。 如果為-1，將等待游標就會結束。

### <a name="remarks"></a>備註

預設實作沙漏游標。 `DoWaitCursor` 會維護參考計數。 當正數時，會顯示沙漏游標。

雖然您不會正常呼叫`DoWaitCursor`直接，您可以覆寫來變更將等待游標，或執行其他處理，而將等待游標會顯示此成員函式。

更簡單、 更有效率的方式來實作等待游標，使用`CWaitCursor`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="enabled2dsupport"></a>  CWinApp::EnableD2DSupport

必須有 Visual Studio 2010 SP1。

可讓應用程式 D2D 支援。 初始化主視窗之前先呼叫這個方法。

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>參數

*d2dFactoryType*<br/>
D2D factory 和它所建立的資源的執行緒模型。

*writeFactoryType*<br/>
值，指定是否將共用或隔離寫入 factory 物件

### <a name="return-value"></a>傳回值

如果 D2D 支援已啟用，則為 FALSE-否則為 true，則傳回

##  <a name="enablehtmlhelp"></a>  CWinApp::EnableHtmlHelp

呼叫此成員函式的建構函式內您`CWinApp`-衍生類別，以使用 HTMLHelp 應用程式的說明。

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>備註

##  <a name="enableshellopen"></a>  CWinApp::EnableShellOpen

通常呼叫此函式，從您`InitInstance`覆寫，可讓您的應用程式使用者當他們連按兩下檔案從 Windows 檔案管理員中開啟資料檔案。

```
void EnableShellOpen();
```

### <a name="remarks"></a>備註

呼叫`RegisterShellFileTypes`成員函式搭配使用，此函式，或提供。REG 檔案與您的應用程式的文件類型的手動註冊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="enabletaskbarinteraction"></a>  CWinApp::EnableTaskbarInteraction

可讓工作列互動。

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定與 Windows 7 工作列互動 (TRUE)，應該啟用或停用 (FALSE)。

### <a name="return-value"></a>傳回值

如果工作列互動可以啟用或停用，則傳回 TRUE。

### <a name="remarks"></a>備註

建立主視窗之前，必須呼叫這個方法，否則它會判斷提示，並傳回 FALSE。

##  <a name="exitinstance"></a>  CWinApp::ExitInstance

由架構呼叫，從`Run`成員函式以結束應用程式的這個執行個體。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>傳回值

應用程式的結束代碼;0 表示沒有錯誤，而大於 0 的值會指出錯誤。 此值做為傳回的值從`WinMain`。

### <a name="remarks"></a>備註

請勿呼叫此成員函式從任何地方但內`Run`成員函式。

此函式的預設實作會寫入應用程式的架構選項。INI 檔案。 覆寫這個函式來清除您的應用程式終止時。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="getapplicationrecoveryparameter"></a>  CWinApp::GetApplicationRecoveryParameter

擷取應用程式的復原方法的輸入的參數。

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>傳回值

應用程式的復原方法預設輸入的參數。

### <a name="remarks"></a>備註

預設行為，此函式會傳回 NULL。

如需詳細資訊，請參閱 < [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。

##  <a name="getapplicationrecoverypinginterval"></a>  CWinApp::GetApplicationRecoveryPingInterval

傳回重新啟動管理員會等到復原回撥函式傳回的時間的長度。

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>傳回值

以毫秒為單位的時間長度。

### <a name="remarks"></a>備註

非預期地向在重新啟動管理員結束應用程式、 應用程式嘗試儲存開啟的文件，並呼叫復原回呼函式。 預設復原回呼函式[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。

架構會等到復原回撥函式傳回長度是時間的 ping 間隔。 您可以藉由覆寫自訂 ping 間隔`CWinApp::GetApplicationRecoveryPingInterval`或藉由提供的自訂值`RegisterWithRestartManager`。

##  <a name="getapplicationrestartflags"></a>  CWinApp::GetApplicationRestartFlags

重新啟動管理員傳回的旗標。

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>傳回值

重新啟動管理員的旗標。 預設實作會傳回 0。

### <a name="remarks"></a>備註

重新啟動管理員的旗標不影響使用的預設實作。 它們僅供未來使用。

當您重新啟動管理員與註冊應用程式使用時，會設定旗標[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。

重新啟動管理員旗標的可能值如下所示：

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="getappregistrykey"></a>  CWinApp::GetAppRegistryKey

傳回的索引鍵的 HKEY_CURRENT_USER\\\RegistryKey\ProfileName 「 軟體 」。

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功; 的應用程式金鑰否則為 NULL。

### <a name="remarks"></a>備註

##  <a name="getdatarecoveryhandler"></a>  CWinApp::GetDataRecoveryHandler

取得應用程式的這個執行個體中的資料復原處理常式。

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>傳回值

應用程式的這個執行個體資料復原處理常式。

### <a name="remarks"></a>備註

重新啟動管理員會使用每個應用程式必須有一個執行個體[CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。 這個類別是負責監視開啟的文件和自動儲存檔案。 行為`CDataRecoveryHandler`重新啟動管理員的組態而定。 如需詳細資訊，請參閱 < [CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。

這個方法會傳回 NULL 在作業系統上早於 Windows Vista。 重新啟動管理員不早於 Windows Vista 支援作業系統上。

如果應用程式目前沒有資料復原處理常式，這個方法會建立一個，並傳回的指標。

##  <a name="getfirstdoctemplateposition"></a>  CWinApp::GetFirstDocTemplatePosition

取得應用程式中的第一個文件範本的位置。

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果清單是空的則為 NULL。

### <a name="remarks"></a>備註

使用位置值傳回呼叫[GetNextDocTemplate](#getnextdoctemplate)若要取得第一個[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件。

##  <a name="gethelpmode"></a>  CWinApp::GetHelpMode

擷取說明應用程式所使用的型別。

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>傳回值

使用應用程式的說明類型。 請參閱[CWinApp::m_eHelpType](#m_ehelptype)如需詳細資訊。

##  <a name="getnextdoctemplate"></a>  CWinApp::GetNextDocTemplate

取得所識別的文件範本*pos*，然後設定*pos*位置值。

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置值的參考`GetNextDocTemplate`或是[GetFirstDocTemplatePosition](#getfirstdoctemplateposition)。 這個呼叫是下一個位置來更新此值。

### <a name="return-value"></a>傳回值

指標[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件。

### <a name="remarks"></a>備註

您可以使用`GetNextDocTemplate`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetFirstDocTemplatePosition`。

您必須確定您位置的值無效。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

最後一個擷取的文件範本是否可用，則新值的*pos*設為 NULL。

##  <a name="getprinterdevicedefaults"></a>  CWinApp::GetPrinterDeviceDefaults

呼叫此成員函式，以準備進行列印的印表機裝置內容。

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>參數

*pPrintDlg*<br/>
指標[PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從 Windows 中擷取目前的印表機預設值。為有需要或會使用上次的印表機設定會設定使用者在 設定列印格式中的 INI 檔案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="getprofilebinary"></a>  CWinApp::GetProfileBinary

呼叫此成員函式，來擷取應用程式的登錄指定的區段內的項目中的二進位資料或。INI 檔案。

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
指向以 null 終止的字串，這個字串指定包含項目的區段。

*lpszEntry*<br/>
指向以 null 終止的字串，其中包含要擷取其值的項目。

*ppData*<br/>
將會收到資料的位址指標指向。

*pBytes*<br/>
為 UINT，將會收到的大小 （以位元組為單位） 的資料點。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式不區分大小寫，因此中的字串*lpszSection*並*lpszEntry*參數可能大小寫不同。

> [!NOTE]
> `GetProfileBinary` 會配置緩衝區，並傳回在其地址\* *ppData*。 呼叫端負責釋放緩衝區使用**delete []**。

> [!IMPORTANT]
> 這個函式傳回的資料不一定是以 NULL 終止，因此，呼叫端必須執行驗證。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

如需其他範例，請參閱 < [CWinApp::WriteProfileBinary](#writeprofilebinary)。

##  <a name="getprofileint"></a>  CWinApp::GetProfileInt

呼叫此成員函式，從應用程式登錄檔或 .INI 檔中指定的區段內的項目擷取整數的值。

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
指向以 null 終止的字串，這個字串指定包含項目的區段。

*lpszEntry*<br/>
指向以 null 終止的字串，其中包含要擷取其值的項目。

*n 預設*<br/>
指定架構找不到項目時要傳回的預設值。

### <a name="return-value"></a>傳回值

如果函式成功，在指定項目後面之字串的整數值。 傳回值是值*n 預設*參數，如果函數找不到項目。 如果對應到指定項目的值不是整數，則傳回值為 0。

此成員函式支援 .INI 檔中值的十六進位標記法。 當您擷取帶正負號的整數時，您應該將值轉換成**int**。

### <a name="remarks"></a>備註

此成員函式不區分大小寫，因此中的字串*lpszSection*並*lpszEntry*參數可能大小寫不同。

> [!IMPORTANT]
> 這個函式傳回的資料不一定是以 NULL 終止，因此，呼叫端必須執行驗證。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

如需其他範例，請參閱 < [cwinapp:: Writeprofileint](#writeprofileint)。

##  <a name="getprofilestring"></a>  CWinApp::GetProfileString

呼叫此成員函式，以擷取應用程式的登錄中指定的區段內的項目相關聯的字串或。INI 檔案。

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
指向以 null 終止的字串，這個字串指定包含項目的區段。

*lpszEntry*<br/>
指向以 null 終止的字串，包含要擷取其字串的項目。 此值必須不是 NULL。

*lpszDefault*<br/>
預設字串值，指定的項目，如果在初始設定檔案中找不到進入點。

### <a name="return-value"></a>傳回值

傳回的值是從應用程式的字串。INI 檔案或*lpszDefault*如果找不到字串。 Framework 所支援的最大字串長度是 _MAX_PATH。 如果*lpszDefault*是 NULL，傳回的值為空字串。

### <a name="remarks"></a>備註

> [!IMPORTANT]
> 這個函式傳回的資料不一定是以 NULL 終止，因此，呼叫端必須執行驗證。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

如需其他範例，請參閱範例[CWinApp::GetProfileInt](#getprofileint)。

##  <a name="getsectionkey"></a>  CWinApp::GetSectionKey

傳回的索引鍵的 HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection 「 軟體 」。

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
若要取得索引鍵的名稱。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則 「 區段 」 索引鍵否則為 NULL。

### <a name="remarks"></a>備註

##  <a name="hideapplication"></a>  CWinApp::HideApplication

呼叫此成員函式，以隱藏應用程式前關閉開啟的文件。

```
void HideApplication();
```

##  <a name="htmlhelp"></a>  CWinApp::HtmlHelp

呼叫此成員函式來叫用 HTMLHelp 應用程式。

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>參數

*dwData*<br/>
指定其他資料。 所使用的值而定的值*nCmd*參數。

*nCmd*<br/>
指定要求的說明類型。 如需可能的值，以及它們如何影響*dwData*參數，請參閱*uCommand*有關 HTMLHelp API 函式在 Windows SDK 中所述的參數。

### <a name="remarks"></a>備註

架構也會呼叫此函式來叫用 HTMLHelp 應用程式。

您的應用程式終止時，架構會自動關閉 HTMLHelp 應用程式。

##  <a name="initinstance"></a>  Cwinapp:: Initinstance

Windows 可讓在相同時間執行的相同程式的多個複本。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>傳回值

如果初始化成功則為非零否則為 0。

### <a name="remarks"></a>備註

應用程式初始化在概念上分成兩個區段： 一次性的應用程式的初始化完成第一次程式執行時，和執行每個執行個體初始化時間一份程式執行，包括第一次。 架構的實作`WinMain`呼叫此函式。

覆寫`InitInstance`來初始化每個 Windows 底下執行的應用程式的新執行個體。 通常，您會覆寫`InitInstance`來建構您的主視窗物件和設定`CWinThread::m_pMainWnd`指向該視窗的資料成員。 如需有關如何覆寫此成員函式的詳細資訊，請參閱 < [CWinApp： 應用程式類別](../../mfc/cwinapp-the-application-class.md)。

> [!NOTE]
> MFC 應用程式必須初始化為單一執行緒 apartment (STA)。 如果您呼叫[CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex)中您`InitInstance`覆寫，請指定 COINIT_APARTMENTTHREADED （而不是 COINIT_MULTITHREADED）。 如需詳細資訊，請參閱 < PRB: MFC 應用程式停止回應時初始化為多執行緒 Apartment （828643） 在應用程式[ http://support.microsoft.com/default.aspxscid=kb; 828643](http://support.microsoft.com/default.aspxscid=kb;828643)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="istaskbarinteractionenabled"></a>  CWinApp::IsTaskbarInteractionEnabled

會告知是否已啟用 Windows 7 工作列互動。

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>傳回值

如果為 true`EnableTaskbarInteraction`已呼叫和作業系統是 Windows 7 或更新版本。

### <a name="remarks"></a>備註

工作列互動表示 MDI 應用程式，會在滑鼠指標移至應用程式的工作列按鈕時，會顯示的個別索引標籤式縮圖中顯示的 MDI 子系內容。

##  <a name="loadcursor"></a>  CWinApp::LoadCursor

載入所命名的資料指標資源*lpszResourceName*或所指定*nIDResource*從目前的可執行檔。

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
指向以 null 終止的字串，包含資料指標資源的名稱。 您可以使用`CString`這個引數。

*nIDResource*<br/>
游標資源的識別碼。 如需資源的清單，請參閱 < [LoadCursor](/windows/desktop/api/winuser/nf-winuser-loadcursora) Windows SDK 中。

### <a name="return-value"></a>傳回值

如果成功則為資料指標控制代碼否則為 NULL。

### <a name="remarks"></a>備註

`LoadCursor` 它先前載入; 時，才會載入記憶體的資料指標否則，它會擷取現有的資源的控制代碼。

使用[LoadStandardCursor](#loadstandardcursor)或是[LoadOEMCursor](#loadoemcursor)存取預先定義的 Windows 資料指標的成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="loadicon"></a>  CWinApp::LoadIcon

載入所命名的圖示資源*lpszResourceName*或所指定*nIDResource*從可執行檔。

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>參數

*lpszResourceName*<br/>
指向以 null 終止的字串，包含圖示資源的名稱。 您也可以使用`CString`這個引數。

*nIDResource*<br/>
圖示資源的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為圖示的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

`LoadIcon` 只有當它先前載入; 時，才會載入圖示否則，它會擷取現有的資源的控制代碼。

您可以使用[LoadStandardIcon](#loadstandardicon)或是[LoadOEMIcon](#loadoemicon)成員函式來存取預先定義的 Windows 圖示。

> [!NOTE]
> 此成員函式會呼叫 Win32 API 函式[LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona)，這只能載入 SM_CXICON 和 SM_CYICON 系統計量值符合其大小的圖示。

##  <a name="loadoemcursor"></a>  CWinApp::LoadOEMCursor

載入 Windows 預先定義的資料指標所指定的資源*nIDCursor*。

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>參數

*nIDCursor*<br/>
**OCR_** 資訊清單常數的識別項，指定預先定義的 Windows 資料指標。 您必須擁有`#define OEMRESOURCE`之前`#include \<afxwin.h>`來取得存取權**OCR_** WINDOWS 中的常數。H.

### <a name="return-value"></a>傳回值

如果成功則為資料指標控制代碼否則為 NULL。

### <a name="remarks"></a>備註

使用`LoadOEMCursor`或是[LoadStandardCursor](#loadstandardcursor)存取預先定義的 Windows 資料指標的成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="loadoemicon"></a>  CWinApp::LoadOEMIcon

載入 Windows 預先定義所指定的圖示資源*nIDIcon*。

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>參數

*nIDIcon*<br/>
**OIC_** 資訊清單常數指定預先定義的 Windows 圖示的識別項。 您必須擁有`#define OEMRESOURCE`之前`#include \<afxwin.h>`若要存取**OIC_** WINDOWS 中的常數。H.

### <a name="return-value"></a>傳回值

如果成功則為圖示的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

使用`LoadOEMIcon`或是[LoadStandardIcon](#loadstandardicon)成員函式來存取預先定義的 Windows 圖示。

##  <a name="loadstandardcursor"></a>  CWinApp::LoadStandardCursor

載入 Windows 預先定義的資料指標的資源， *lpszCursorName*指定。

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>參數

*lpszCursorName*<br/>
**IDC_** 資訊清單常數的識別項，指定預先定義的 Windows 資料指標。 在 WINDOWS 中定義這些識別項。H. 下列清單顯示可能的預先定義的值和意義*lpszCursorName*:

- 標準 IDC_ARROW 的箭號游標

- IDC_IBEAM 標準文字插入資料指標

- Windows 會執行耗時的工作時所使用的 IDC_WAIT 沙漏游標

- IDC_CROSS 交叉線的資料指標選取範圍

- 直接註冊的 IDC_UPARROW 箭號

- IDC_SIZE 過時和不受支援;使用 IDC_SIZEALL

- IDC_SIZEALL A 四指向箭號。 要用於調整視窗大小的游標。

- IDC_ICON 過時和不受支援。 使用 IDC_ARROW。

- IDC_SIZENWSE 雙箭號與結尾位置左上方和較低權限

- IDC_SIZENESW 雙箭號與向右鍵和較低的左上方的結尾

- IDC_SIZEWE 水平的雙箭號

- IDC_SIZENS 垂直的雙箭號

### <a name="return-value"></a>傳回值

如果成功則為資料指標控制代碼否則為 NULL。

### <a name="remarks"></a>備註

使用`LoadStandardCursor`或是[LoadOEMCursor](#loadoemcursor)存取預先定義的 Windows 資料指標的成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="loadstandardicon"></a>  CWinApp::LoadStandardIcon

載入 Windows 預先定義的圖示資源， *lpszIconName*指定。

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>參數

*lpszIconName*<br/>
指定預先定義的 Windows 圖示資訊清單常數識別碼。 在 WINDOWS 中定義這些識別項。H. 可能的預先定義的值及其描述的清單，請參閱*lpIconName*中的參數[LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona) Windows SDK 中。

### <a name="return-value"></a>傳回值

如果成功則為圖示的控制代碼否則為 NULL。

### <a name="remarks"></a>備註

使用`LoadStandardIcon`或是[LoadOEMIcon](#loadoemicon)成員函式來存取預先定義的 Windows 圖示。

##  <a name="loadstdprofilesettings"></a>  CWinApp::LoadStdProfileSettings

呼叫此成員函式內[InitInstance](#initinstance)成員函式來啟用與載入最近使用過的 (MRU) 檔案的清單和上一次預覽狀態。

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>參數

*nMaxMRU*<br/>
要追蹤最近使用過的檔案數目。

### <a name="remarks"></a>備註

如果*nMaxMRU*是 0，則會維持沒有 MRU 清單。

##  <a name="m_bhelpmode"></a>  CWinApp::m_bHelpMode

如果應用程式中 （依慣例以叫用 SHIFT + F1）; 的說明內容模式，則為 TRUE。否則為 FALSE。

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>備註

在說明內容模式，游標會變成一個問號，則使用者可以移動它關於畫面。 如果您想要實作特殊處理，在說明模式時，請檢查此旗標。 `m_bHelpMode` 是 BOOL 類型的公用變數。

##  <a name="m_dwrestartmanagersupportflags"></a>  CWinApp::m_dwRestartManagerSupportFlags

決定重新啟動管理員的運作方式的旗標。

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>備註

若要啟用重新啟動管理員，將`m_dwRestartManagerSupportFlags`至您想要的行為。 下表顯示可用的旗標。

|||
|-|-|
|旗標|描述|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|使用註冊該應用程式[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)。 重新啟動管理員會負責重新啟動應用程式，如果非預期地結束。|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|重新啟動管理員與註冊應用程式，並重新啟動應用程式時，重新啟動管理員會呼叫復原回呼函式。 預設復原回呼函式[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|啟用 自動儲存並重新啟動管理員時，自動儲存任何開啟的文件時重新啟動應用程式。|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|啟用 自動儲存並重新啟動管理員時，自動儲存任何開啟的文件以固定間隔。 所定義的間隔[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)。|
|-AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|重新啟動管理員重新啟動非預期的結束應用程式之後，開啟先前開啟的文件。 [CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)處理儲存開啟的文件的清單，以及還原它們。|
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|重新啟動管理員會提示使用者將會檔案還原之後重新啟動應用程式。 `CDataRecoveryHandler`類別向使用者查詢。|
|-AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|AFX_RESTART_MANAGER_SUPPORT_RESTART AFX_RESTART_MANAGER_SUPPORT_RECOVER 及 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 的聯集。|
|-AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE 及 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL，AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 的聯集。|
|-AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_RESTART 及 AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES，AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES 的聯集。|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|等位的 ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY、 AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL、 AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES 和 AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。|

##  <a name="m_ehelptype"></a>  CWinApp::m_eHelpType

此資料成員的類型是列舉型別 AFX_HELP_TYPE，其定義內`CWinApp`類別。

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>備註

AFX_HELP_TYPE 列舉型別定義，如下所示：

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- 若要設定應用程式的 HTML 說明的說明，請呼叫[SetHelpMode](#sethelpmode)並指定`afxHTMLHelp`。

- 若要設定 WinHelp 應用程式的說明，請呼叫`SetHelpMode`並指定`afxWinHelp`。

##  <a name="m_hinstance"></a>  CWinApp::m_hInstance

對應至*hInstance*參數傳遞至 Windows `WinMain`。

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>備註

`m_hInstance`資料成員是在 Windows 下執行的應用程式的目前執行個體的控制代碼。 這由全域函式[AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)。 `m_hInstance` 是型別 HINSTANCE 的公用變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="m_lpcmdline"></a>  CWinApp::m_lpCmdLine

對應至*lpCmdLine*參數傳遞至 Windows `WinMain`。

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>備註

指向以 null 終止的字串，指定命令列應用程式。 使用`m_lpCmdLine`使用者輸入應用程式啟動時存取任何命令列引數。 `m_lpCmdLine` 是 LPTSTR 類型的公用變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="m_nautosaveinterval"></a>  CWinApp::m_nAutosaveInterval

以毫秒為單位時，自動儲存之間的時間長度。

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>備註

您可以設定自動儲存開啟的文件的重新啟動管理員設定的間隔。 如果您的應用程式不自動儲存檔，此參數沒有任何作用。

##  <a name="m_ncmdshow"></a>  CWinApp::m_nCmdShow

對應至*nCmdShow*參數傳遞至 Windows `WinMain`。

```
int m_nCmdShow;
```

### <a name="remarks"></a>備註

您應傳入`m_nCmdShow`做為引數，當您呼叫[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)針對您的應用程式主視窗。 `m_nCmdShow` 這類型的公用變數**int**。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="m_pactivewnd"></a>  CWinApp::m_pActiveWnd

您可以使用此資料成員來儲存具有您 OLE 伺服器應用程式就地啟動 OLE 容器應用程式的主視窗的指標。

### <a name="remarks"></a>備註

如果此資料成員為 NULL，但應用程式不是就地啟用作用中。

框架視窗時就地啟動 OLE 容器應用程式，架構就會設定這個成員變數。

##  <a name="m_pdatarecoveryhandler"></a>  CWinApp::m_pDataRecoveryHandler

應用程式的資料復原處理常式的指標。

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>備註

應用程式的資料復原處理常式會監視開啟的文件和時，自動儲存它們。 架構會使用資料復原處理常式，它在非預期地結束之後，重新啟動應用程式時，還原會檔案。 如需詳細資訊，請參閱 < [CDataRecoveryHandler 類別](../../mfc/reference/cdatarecoveryhandler-class.md)。

##  <a name="m_pszappname"></a>  CWinApp::m_pszAppName

指定應用程式的名稱。

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>備註

應用程式名稱可以來自傳遞給參數[CWinApp](#cwinapp)建構函式，或者，如果未指定識別碼的 AFX_IDS_APP_TITLE 資源字串。 如果資源中找不到應用程式名稱，其來自該程式。EXE 檔案名稱。

全域函式所傳回[AfxGetAppName](application-information-and-management.md#afxgetappname)。 `m_pszAppName` 這類型的公用變數**const char**<strong>\*</strong>。

> [!NOTE]
> 如果您將值指派給`m_pszAppName`，它必須以動態方式配置到堆積上。 `CWinApp`解構函式呼叫**免費**> （) 與這個指標。 您有許多想要使用`_tcsdup`（） 執行階段程式庫函式，進行配置。 此外，釋放記憶體指派新值之前，與目前的指標相關聯。 例如: 

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="m_pszexename"></a>  CWinApp::m_pszExeName

包含不含副檔名的應用程式的可執行檔的名稱。

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>備註

不同於[m_pszAppName](#m_pszappname)，此名稱不能包含空格。 `m_pszExeName` 這類型的公用變數**const char**<strong>\*</strong>。

> [!NOTE]
> 如果您將值指派給`m_pszExeName`，它必須以動態方式配置到堆積上。 `CWinApp`解構函式呼叫**免費**> （) 與這個指標。 您有許多想要使用`_tcsdup`（） 執行階段程式庫函式，進行配置。 此外，釋放記憶體指派新值之前，與目前的指標相關聯。 例如: 

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="m_pszhelpfilepath"></a>  CWinApp::m_pszHelpFilePath

包含應用程式的說明檔的路徑。

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>備註

根據預設，架構會初始化`m_pszHelpFilePath`的應用程式名稱 」。HLP"附加。 若要變更說明檔的名稱，請設定`m_pszHelpFilePath`指向包含所需的說明檔的完整名稱的字串。 若要這樣做的方便位置是在應用程式的[InitInstance](#initinstance)函式。 `m_pszHelpFilePath` 這類型的公用變數**const char**<strong>\*</strong>。

> [!NOTE]
> 如果您將值指派給`m_pszHelpFilePath`，它必須以動態方式配置到堆積上。 `CWinApp`解構函式呼叫**免費**> （) 與這個指標。 您有許多想要使用`_tcsdup`（） 執行階段程式庫函式，進行配置。 此外，釋放記憶體指派新值之前，與目前的指標相關聯。 例如: 

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName

包含應用程式的名稱。INI 檔案。

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>備註

`m_pszProfileName` 這類型的公用變數**const char**<strong>\*</strong>。

> [!NOTE]
> 如果您將值指派給`m_pszProfileName`，它必須以動態方式配置到堆積上。 `CWinApp`解構函式呼叫**免費**> （) 與這個指標。 您有許多想要使用`_tcsdup`（） 執行階段程式庫函式，進行配置。 此外，釋放記憶體指派新值之前，與目前的指標相關聯。 例如: 

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="m_pszregistrykey"></a>  CWinApp::m_pszRegistryKey

用來判斷，在登錄或 INI 檔案中，應用程式設定檔設定的儲存位置。

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>備註

一般來說，這個資料成員都會被視為唯讀。

- 值會儲存至登錄機碼。 應用程式設定檔設定的名稱會附加至下列登錄機碼： HKEY_CURRENT_USER/軟體/LocalAppWizard 產生 /。

如果您將值指派給`m_pszRegistryKey`，它必須以動態方式配置到堆積上。 `CWinApp`解構函式呼叫**免費**> （) 與這個指標。 您有許多想要使用`_tcsdup`（） 執行階段程式庫函式，進行配置。 此外，釋放記憶體指派新值之前，與目前的指標相關聯。 例如: 

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID

應用程式使用者模型識別碼。

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>備註

##  <a name="oncontexthelp"></a>  CWinApp::OnContextHelp

處理應用程式內的 SHIFT + F1 說明。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )`陳述式，以您`CWinApp`類別訊息對應，以及將快速鍵對應表項目，通常是 SHIFT + F1，以啟用此成員函式。

`OnContextHelp` 會將說明模式的應用程式。 游標會變為有箭號和問號和使用者可以將滑鼠指標並按下滑鼠左的按鈕來選取 對話方塊、 視窗、 功能表或命令按鈕。 此成員函式會擷取游標下的物件說明內容，並呼叫 Windows 函式 WinHelp 以該說明內容。

##  <a name="onddecommand"></a>  CWinApp::OnDDECommand

由架構呼叫，當主框架視窗收到 DDE 執行訊息。

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>參數

*lpszCommand*<br/>
指向應用程式所收到的 DDE 命令字串。

### <a name="return-value"></a>傳回值

非零值，如果命令處理;否則為 0。

### <a name="remarks"></a>備註

預設實作會檢查是否命令是要開啟的文件的要求，是否是的話，便會開啟指定的文件。 當使用者按兩下資料檔案時，Windows 檔案管理員通常會傳送這類的 DDE 命令字串。 此函式以處理其他 DDE 執行命令，例如列印命令覆寫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="onfilenew"></a>  CWinApp::OnFileNew

會實作 ID_FILE_NEW 命令。

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_FILE_NEW, OnFileNew )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 如果啟用，此函式會處理新檔案的命令執行。

請參閱[技術提示 22](../../mfc/tn022-standard-commands-implementation.md)的預設行為，以及有關如何覆寫此成員函式的指引的資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileopen"></a>  CWinApp::OnFileOpen

會實作 ID_FILE_OPEN 命令。

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_FILE_OPEN, OnFileOpen )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 如果啟用，此函式會處理開啟檔案命令執行。

如需預設行為的詳細資訊和如何覆寫此成員函式的指引，請參閱[技術提示 22](../../mfc/tn022-standard-commands-implementation.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileprintsetup"></a>  CWinApp::OnFilePrintSetup

會實作 ID_FILE_PRINT_SETUP 命令。

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 如果啟用，此函式會處理執行檔案列印命令。

如需預設行為的詳細資訊和如何覆寫此成員函式的指引，請參閱[技術提示 22](../../mfc/tn022-standard-commands-implementation.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onhelp"></a>  CWinApp::OnHelp

在應用程式 (使用目前的內容) 中處理 F1 說明。

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>備註

通常您也會加入項目快速鍵 F1 鍵。 啟用的 F1 鍵是只使用慣例，不是需求。

您必須新增`ON_COMMAND( ID_HELP, OnHelp )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 如果啟用，由架構呼叫時使用者按下 F1 鍵。

此訊息處理常式函式的預設實作會判斷對應至目前的視窗、 對話方塊中或功能表項目，然後再呼叫 WINHELP 的說明內容。EXE。 如果目前沒有內容，則此函數會使用預設的內容。

覆寫這個成員函式設為 「 說明 」 內容以外的視窗、 對話方塊、 功能表項目或目前具有焦點的工具列按鈕。 呼叫`WinHelp`與需要說明內容識別碼。

##  <a name="onhelpfinder"></a>  CWinApp::OnHelpFinder

處理 ID_HELP_FINDER 和 ID_DEFAULT_HELP 命令。

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 如果啟用，架構會呼叫此訊息處理常式函式應用程式的使用者選取要叫用協助搜尋命令時`WinHelp`標準**HELP_FINDER**主題。

##  <a name="onhelpindex"></a>  CWinApp::OnHelpIndex

處理 ID_HELP_INDEX 命令，並提供預設的說明主題。

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 如果啟用，架構會呼叫此訊息處理常式函式應用程式的使用者選取要叫用說明索引命令時`WinHelp`標準**HELP_INDEX**主題。

##  <a name="onhelpusing"></a>  CWinApp::OnHelpUsing

處理 ID_HELP_USING 命令。

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>備註

您必須新增`ON_COMMAND( ID_HELP_USING, OnHelpUsing )`陳述式，以您`CWinApp`類別訊息對應，以啟用此成員函式。 當您的應用程式的使用者選取叫用的說明使用命令時，架構會呼叫此訊息處理常式函式`WinHelp`應用程式與標準**HELP_HELPONHELP**主題。

##  <a name="onidle"></a>  CWinApp::OnIdle

若要執行閒置時間處理此成員函式會覆寫。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>參數

*lCount*<br/>
每次遞增計數器`OnIdle`應用程式的訊息佇列是空的時呼叫。 這個計數會重設為 0 每次處理新訊息時。 您可以使用*lCount*參數，來判斷相對的應用程式已閒置而不處理訊息的時間長度。

### <a name="return-value"></a>傳回值

非零值，以接收更多閒置處理時間;如果沒有更多的閒置時間需要，0。

### <a name="remarks"></a>備註

`OnIdle` 預設訊息迴圈中時呼叫應用程式的訊息佇列是空的。 使用覆寫來呼叫您自己的背景工作閒置處理常式。

`OnIdle` 應該會傳回 0，表示所需的任何閒置的處理時間。 *LCount*參數就會遞增每次`OnIdle`時的訊息佇列是空的並重設為 0，因此每次處理新訊息時呼叫。 您可以呼叫您不同的閒置常式，此計數為基礎。

閒置迴圈處理彙總如下：

1. 如果 Microsoft Foundation 類別程式庫中的訊息迴圈會檢查訊息佇列，並尋找沒有擱置的訊息，則會呼叫`OnIdle`應用程式物件和提供 0 作為*lCount*引數。

2. `OnIdle` 執行一些處理，並傳回非零值，指出它應該再次呼叫以執行進一步處理。

3. 訊息迴圈會檢查訊息佇列一次。 如果沒有訊息擱置，它會呼叫`OnIdle`同樣地，遞增*lCount*引數。

4. 最後，`OnIdle`完成處理所有其閒置的工作，並傳回 0。 這會告知訊息迴圈，以停止呼叫`OnIdle`直到下一個訊息收到的訊息佇列，此時閒置的循環會以重新啟動設定為 0 的引數。

不執行冗長的工作期間`OnIdle`因為您的應用程式無法處理使用者輸入，直到`OnIdle`傳回。

> [!NOTE]
> 預設實作`OnIdle`更新命令的使用者介面物件，例如功能表項目和工具列按鈕，而它執行清除內部的資料結構。 因此，如果您覆寫`OnIdle`，您必須呼叫`CWinApp::OnIdle`與`lCount`在您覆寫的版本中。 第一次呼叫閒置處理的所有基底類別 (亦即，直到基底類別`OnIdle`會傳回 0)。 如果您需要執行的工作，基底類別處理完成之前，檢閱 選取適當的基底類別實作*lCount*期間用來執行工作。

如果您不想`OnIdle`被呼叫，從訊息佇列擷取訊息時，您可以覆寫[CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage)。 如果應用程式已設定非常短的計時器，或如果系統正在 WM_SYSTIMER 訊息，然後`OnIdle`會重複呼叫，而且會降低效能。

### <a name="example"></a>範例

下列兩個範例示範如何使用`OnIdle`。 第一個範例會處理兩個閒置的工作，使用*lCount*引數來排定工作的優先順序。 第一項工作是高優先順序，並且應該盡可能。 第二項工作並沒有那麼重要，應該只在使用者輸入的長時間暫停時，才能完成。 請注意呼叫的基底類別版本`OnIdle`。 第二個範例會管理一組具有不同優先順序的閒置工作。

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="opendocumentfile"></a>  CWinApp::OpenDocumentFile

架構會呼叫這個方法，以開啟的具名[CDocument](../../mfc/reference/cdocument-class.md)應用程式檔案。

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
[in]要開啟之檔案的名稱。

*bAddToMRU*<br/>
[in]TRUE 表示在文件是其中一個最新的檔案;FALSE 表示文件不是其中一個最新的檔案。

### <a name="return-value"></a>傳回值

指標`CDocument`如果成功，否則為 NULL。

### <a name="remarks"></a>備註

如果已開啟具有該名稱的文件，則包含該文件的第一個框架視窗會收到焦點。 如果應用程式支援多個文件範本，架構會使用找到適當的文件範本嘗試載入文件的副檔名。 如果成功，文件範本則會建立框架視窗和文件的檢視。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="parsecommandline"></a>  CWinApp::ParseCommandLine

呼叫此成員函式，來剖析命令列，並傳送至參數，一次[CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)。

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>參數

*rCmdInfo*<br/>
參考[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)物件。

### <a name="remarks"></a>備註

當您啟動新的 MFC 專案，使用應用程式精靈時，應用程式精靈將建立的本機執行個體`CCommandLineInfo`，然後呼叫`ProcessShellCommand`並`ParseCommandLine`中[InitInstance](#initinstance)成員函式。 命令列會遵循以下所述的路由：

1. 在建立後`InitInstance`，則`CCommandLineInfo`物件傳遞給`ParseCommandLine`。

2. `ParseCommandLine` 然後呼叫`CCommandLineInfo::ParseParam`重複一次，每個參數。

3. `ParseParam` 填滿`CCommandLineInfo`物件，然後傳遞給[會發生於 ProcessShellCommand](#processshellcommand)。

4. `ProcessShellCommand` 處理命令列引數和旗標。

請注意，您可以呼叫`ParseCommandLine`視直接。

如需命令列的旗標的描述，請參閱 < [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)。

##  <a name="pretranslatemessage"></a>  CWinApp::PreTranslateMessage

覆寫這個函式來篩選視窗訊息，再將它們分派至 Windows 函式[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)的預設實作會執行對應鍵轉譯，因此您必須呼叫`CWinApp::PreTranslateMessage`您覆寫的版本中的成員函式。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
指標[MSG](../../mfc/reference/msg-structure1.md)結構，其中包含要處理的訊息。

### <a name="return-value"></a>傳回值

如果訊息已完全處理中為非零`PreTranslateMessage`，不應進一步處理。 如果應該以一般方式處理訊息，則為零。

##  <a name="processmessagefilter"></a>  CWinApp::ProcessMessageFilter

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
Windows 的指標[MSG](../../mfc/reference/msg-structure1.md)結構。

### <a name="return-value"></a>傳回值

如果訊息已處理，非零值。否則為 0。

### <a name="remarks"></a>備註

攔截函式會處理傳送至應用程式的一般訊息之前的事件處理。

如果您覆寫此進階的功能，請務必呼叫基底類別版本，以維護的架構連接處理。

##  <a name="processshellcommand"></a>  CWinApp::ProcessShellCommand

此成員函式會呼叫[InitInstance](#initinstance)接受從傳遞的參數`CCommandLineInfo`所識別的物件*rCmdInfo*，並執行指定的動作。

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>參數

*rCmdInfo*<br/>
參考[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)物件。

### <a name="return-value"></a>傳回值

如果 shell 命令已成功處理為非零。 如果 0，則傳回 FALSE，從[InitInstance](#initinstance)。

### <a name="remarks"></a>備註

當您啟動新的 MFC 專案，使用應用程式精靈時，應用程式精靈將建立的本機執行個體`CCommandLineInfo`，然後呼叫`ProcessShellCommand`並[ParseCommandLine](#parsecommandline)在`InitInstance`成員函式。 命令列會遵循以下所述的路由：

1. 在建立後`InitInstance`，則`CCommandLineInfo`物件傳遞給`ParseCommandLine`。

2. `ParseCommandLine` 然後呼叫[CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)重複一次，每個參數。

3. `ParseParam` 填滿`CCommandLineInfo`物件，然後傳遞至`ProcessShellCommand`。

4. `ProcessShellCommand` 處理命令列引數和旗標。

資料成員`CCommandLineInfo`所識別的物件[CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)，下列的列舉類型，其定義內的`CCommandLineInfo`類別。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

這些值各自的簡短描述，請參閱`CCommandLineInfo::m_nShellCommand`。

##  <a name="processwndprocexception"></a>  CWinApp::ProcessWndProcException

每當處理常式不會攔截在其中一個應用程式的訊息或命令處理常式中擲回例外狀況時，架構會呼叫此成員函式。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>參數

*e*<br/>
無法攔截的例外狀況的指標。

*pMsg*<br/>
A [MSG](../../mfc/reference/msg-structure1.md)結構，其中包含導致擲回例外狀況架構的 windows 訊息的相關資訊。

### <a name="return-value"></a>傳回值

應該傳回給 Windows 值。 通常這是 0l windows 訊息，1l (TRUE) 的命令訊息。

### <a name="remarks"></a>備註

請勿直接呼叫此成員函式。

此成員函式的預設實作會建立一個訊息方塊。 如果無法攔截的例外狀況是使用功能表、 工具列或快速鍵命令失敗，訊息方塊會顯示 「 命令失敗 」 的訊息;否則，它會顯示 「 應用程式內部錯誤 」 訊息。

覆寫此成員函式，來提供全域處理您的例外狀況。 如果您想要顯示訊息方塊，只能呼叫基底功能。

##  <a name="register"></a>  CWinApp::Register

執行不會處理任何註冊工作`RegisterShellFileTypes`。

```
virtual BOOL Register();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

預設實作只會傳回 TRUE。 覆寫此函式可提供任何自訂的註冊步驟。

##  <a name="registershellfiletypes"></a>  CWinApp::RegisterShellFileTypes

呼叫此成員函式，以註冊您的應用程式的文件類型的所有使用 Windows 檔案管理員。

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>參數

*bCompat*<br/>
[in]TRUE 會將列印和列印至，允許使用者列印檔案，直接從殼層，或將檔案拖曳至印表機物件的殼層命令的登錄項目。 它也會新增 DefaultIcon 索引鍵。 根據預設，此參數為 FALSE 的回溯相容性。

### <a name="remarks"></a>備註

這可讓使用者開啟按兩下它從檔案管理員中建立您的應用程式的資料檔案。 呼叫`RegisterShellFileTypes`呼叫之後[Initinstance](#adddoctemplate)針對每個應用程式中的文件範本。 同時也呼叫[EnableShellOpen](#enableshellopen)成員函式呼叫時`RegisterShellFileTypes`。

`RegisterShellFileTypes` 逐一查看清單[CDocTemplate](../../mfc/reference/cdoctemplate-class.md) ，應用程式維護和物件，每個文件範本，將項目加入至註冊資料庫，Windows 會維護檔案關聯。 檔案管理員會使用這些項目來開啟資料檔案，當使用者按兩下它。 這就不需要寄送。您的應用程式的登錄檔案。

> [!NOTE]
> `RegisterShellFileTypes` 只有在使用者以系統管理員權限執行程式。 如果程式沒有系統管理員權限，它就無法改變登錄機碼。

如果已註冊的資料庫會將指定的檔案的副檔名關聯另一種檔案類型中，會建立新的關聯。 請參閱`CDocTemplate`格式的字串來註冊這項資訊所需的類別。

##  <a name="registerwithrestartmanager"></a>  CWinApp::RegisterWithRestartManager

重新啟動管理員會向應用程式。

```
virtual HRESULT RegisterWithRestartManager(
    BOOL bRegisterRecoveryCallback,
    const CString& strRestartIdentifier);

virtual HRESULT RegisterWithRestartManager(
    LPCWSTR pwzCommandLineArgs,
    DWORD dwRestartFlags,
    APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,
    LPVOID lpvParam,
    DWORD dwPingInterval,
    DWORD dwCallbackFlags);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*bRegisterRecoveryCallback*|[in]TRUE 表示此執行個體的應用程式會使用復原的回呼函式;FALSE 表示不。 應用程式意外結束時，架構會呼叫復原回呼函式。 如需詳細資訊，請參閱 < [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|
|*strRestartIdentifier*|[in]識別此執行個體重新啟動管理員的唯一字串。 重新啟動管理員識別項是唯一的應用程式的每個執行個體。|
|*pwzCommandLineArgs*|[in]字串，包含任何額外的引數，從命令列。|
|*dwRestartFlags*|[in]重新啟動管理員的選擇性旗標。 如需詳細資訊，請參閱＜備註＞一節。|
|*pRecoveryCallback*|[in]復原的回呼函式。 此函式必須採用 LPVOID 參數做為輸入，並傳回 DWORD。 預設復原回呼函式是`CWinApp::ApplicationRecoveryCallback`。|
|*lpvParam*|[in]復原回撥函式的輸入的參數。 如需詳細資訊，請參閱 < [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)。|
|*dwPingInterval*|[in]重新啟動管理員會等到復原回撥函式傳回的時間長度。 這個參數是以毫秒為單位。|
|*dwCallbackFlags*|[in]旗標傳遞至復原的回呼函式。 保留供未來使用。|

### <a name="return-value"></a>傳回值

S_OK，如果方法成功，否則為錯誤碼。

### <a name="remarks"></a>備註

如果您的應用程式會使用預設的 MFC 實作自動儲存檔案，您應該使用的簡單版本`RegisterWithRestartManager`。 使用複雜版本`RegisterWithRestartManager`如果您想要自訂您的應用程式的自動儲存行為。

如果您呼叫這個方法取代為空字串，如*strRestartIdentifier*，`RegisterWithRestartManager`管理員建立的重新啟動此執行個體的唯一識別項字串。

當應用程式意外結束時，重新啟動管理員會重新啟動從命令列應用程式，並提供唯一的重新啟動做為選擇性的引數的識別碼。 在此案例中，架構會呼叫`RegisterWithRestartManager`兩次。 第一個呼叫是來自[cwinapp:: Initinstance](#initinstance)與字串識別碼為空字串。 然後，此方法[CWinApp::ProcessShellCommand](#processshellcommand)呼叫`RegisterWithRestartManager`使用唯一的重新啟動的識別碼。

重新啟動管理員 」 中向應用程式之後，重新啟動管理員會監視應用程式。 如果應用程式意外結束，重新啟動管理員會呼叫關閉程序期間復原回呼函式。 重新啟動管理員等候*dwPingInterval*復原回呼函式的回應。 如果復原的回呼函式不會回應此時間內，在應用程式會結束而不需執行復原的回呼函式。

根據預設，dwRestartFlags 不支援，但僅供未來使用。 可能值*dwRestartFlags*如下所示：

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="reopenpreviousfilesatrestart"></a>  CWinApp::ReopenPreviousFilesAtRestart

決定是否重新啟動管理員會重新開啟應用程式意外結束時所開啟的檔案。

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理員會重新開啟先前開啟的檔案;FALSE 表示不重新啟動管理員。

##  <a name="restartinstance"></a>  CWinApp::RestartInstance

處理重新啟動管理員啟動應用程式重新啟動。

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>傳回值

如果資料復原處理常式會開啟先前開啟的文件，則為 TRUE如果資料復原處理常式發生錯誤，或者如果不有任何先前開啟的文件，則為 FALSE。

### <a name="remarks"></a>備註

當重新啟動管理員重新啟動應用程式時，架構會呼叫這個方法。 這個方法會擷取的資料復原處理常式，並還原會檔案。 這個方法會呼叫[CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments)來判斷使用者是否想要還原會檔案。

這個方法會傳回 FALSE，如果[CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md)決定已開啟的文件。 如果有任何開啟的文件，應用程式通常啟動。

##  <a name="restoreautosavedfilesatrestart"></a>  CWinApp::RestoreAutosavedFilesAtRestart

決定是否重新啟動管理員會將檔案還原重新啟動應用程式時。

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理員會將檔案還原;FALSE 表示不重新啟動管理員。

##  <a name="run"></a>  Cwinapp:: Run

提供預設訊息迴圈。

```
virtual int Run();
```

### <a name="return-value"></a>傳回值

**Int**所傳回的值`WinMain`。

### <a name="remarks"></a>備註

`Run` 取得，並會將 Windows 訊息分派，直到應用程式收到的 WM_QUIT 訊息。 如果應用程式的訊息佇列目前不包含的任何訊息，`Run`呼叫[OnIdle](#onidle)執行閒置時間處理。 內送訊息會移至[PreTranslateMessage](#pretranslatemessage)成員函式進行特殊處理，然後 Windows 函式`TranslateMessage`標準鍵盤轉譯; 最後，`DispatchMessage`呼叫 Windows 函式。

`Run` 很少會覆寫，但您可以覆寫它，以提供特殊的行為。

##  <a name="runautomated"></a>  CWinApp::RunAutomated

呼叫此函式，以判斷是否 「 **/Automation**「 或 」 **-自動化**」 選項已存在，表示用戶端應用程式是否已啟動伺服器應用程式。

```
BOOL RunAutomated();
```

### <a name="return-value"></a>傳回值

非零值，如果找不到選項;否則為 0。

### <a name="remarks"></a>備註

如果有的話，是從命令列移除的選項。 如需有關 OLE Automation 的詳細資訊，請參閱文章[Automation 伺服程式](../../mfc/automation-servers.md)。

##  <a name="runembedded"></a>  CWinApp::RunEmbedded

呼叫此函式，以判斷是否 「 **/內嵌**「 或 」 **-內嵌**」 選項已存在，表示用戶端應用程式是否已啟動伺服器應用程式。

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>傳回值

非零值，如果找不到選項;否則為 0。

### <a name="remarks"></a>備註

如果有的話，是從命令列移除的選項。 如需有關內嵌的詳細資訊，請參閱文章[伺服器： 實作伺服器](../../mfc/servers-implementing-a-server.md)。

##  <a name="saveallmodified"></a>  CWinApp::SaveAllModified

由架構應用程式的主框架視窗關閉時儲存所有文件，或透過 WM_QUERYENDSESSION 訊息呼叫。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>傳回值

安全地終止應用程式; 如果為非零0，表示終止應用程式不安全。

### <a name="remarks"></a>備註

此成員函式的預設實作會呼叫[CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified)針對應用程式中所有修改過的文件的成員函式。

##  <a name="selectprinter"></a>  CWinApp::SelectPrinter

呼叫此成員函式，以選取特定的印表機，並釋放先前已選取 [列印] 對話方塊中的印表機。

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>參數

*hDevNames*<br/>
控制代碼[DEVNAMES](../../mfc/reference/devnames-structure.md)識別驅動程式、 裝置及特定印表機的輸出連接埠名稱的結構。

*hDevMode*<br/>
控制代碼[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)結構，指定裝置初始化和印表機的環境的相關資訊。

*bFreeOld*<br/>
釋放先前選取的印表機。

### <a name="remarks"></a>備註

如果兩個*hDevMode*並*hDevNames*都是 NULL，`SelectPrinter`會使用目前的預設印表機。

##  <a name="sethelpmode"></a>  CWinApp::SetHelpMode

設定應用程式的說明類型。

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>參數

*eHelpType*<br/>
指定要使用的說明類型。 請參閱[CWinApp::m_eHelpType](#m_ehelptype)如需詳細資訊。

### <a name="remarks"></a>備註

設定應用程式的說明類型。

若要設定 HTMLHelp 應用程式的說明類型，您可以呼叫[EnableHTMLHelp](#enablehtmlhelp)。 一旦您呼叫`EnableHTMLHelp`，您的應用程式必須使用 HTMLHelp，作為其說明應用程式。 如果您想要使用 WinHelp 變更，您可以呼叫`SetHelpMode`並設定*eHelpType*至`afxWinHelp`。

##  <a name="setregistrykey"></a>  CWinApp::SetRegistryKey

會儲存在登錄中，而不是 INI 檔案的應用程式設定。

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>參數

*lpszRegistryKey*<br/>
包含索引鍵名稱的字串指標。

*nIDRegistryKey*<br/>
包含的登錄機碼名稱的字串資源的識別碼。

### <a name="remarks"></a>備註

此函式會將*m_pszRegistryKey*，然後可由`GetProfileInt`， `GetProfileString`， `WriteProfileInt`，和`WriteProfileString`的成員函式`CWinApp`。 如果已呼叫此函式之最近使用 (的 MRU) 檔案的清單也會儲存在登錄中。 登錄機碼通常是公司的名稱。 它會儲存在下列形式的索引鍵： HKEY_CURRENT_USER\Software\\< 公司名稱\>\\< 應用程式名稱\>\\< 區段名稱\>\\< 值名稱\>。

##  <a name="supportsapplicationrecovery"></a>  CWinApp::SupportsApplicationRecovery

決定是否重新啟動管理員復原意外結束的應用程式。

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理員復原應用程式。FALSE 表示不重新啟動管理員。

##  <a name="supportsautosaveatinterval"></a>  CWinApp::SupportsAutosaveAtInterval

決定是否重新啟動管理員時，自動儲存開啟的文件以固定間隔。

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理員時，自動儲存開啟的文件;FALSE 表示不重新啟動管理員。

##  <a name="supportsautosaveatrestart"></a>  CWinApp::SupportsAutosaveAtRestart

決定是否重新啟動管理員時，自動儲存任何開啟的文件時重新啟動應用程式。

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示重新啟動管理員時，自動儲存開啟的文件，當應用程式重新啟動;FALSE 表示不重新啟動管理員。

##  <a name="supportsrestartmanager"></a>  CWinApp::SupportsRestartManager

判斷應用程式是否支援重新啟動管理員。

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>傳回值

TRUE 表示此應用程式支援重新啟動管理員;FALSE 表示應用程式則否。

##  <a name="unregister"></a>  CWinApp::Unregister

取消註冊應用程式物件所註冊的所有檔案。

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

`Unregister`函式會復原應用程式物件所執行的註冊和[註冊](#register)函式。 一般來說，這兩個函式會隱含地呼叫 MFC 的因此不會出現在您的程式碼。

覆寫這個函式來執行的自訂移除註冊步驟。

##  <a name="unregistershellfiletypes"></a>  CWinApp::UnregisterShellFileTypes

呼叫此成員函式，若要取消註冊的所有應用程式的文件類型與 Windows 檔案管理員。

```
void UnregisterShellFileTypes();
```

##  <a name="winhelp"></a>  CWinApp::WinHelp

呼叫此成員函式來叫用 WinHelp 應用程式。

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>參數

*dwData*<br/>
指定其他資料。 所使用的值而定的值*nCmd*參數。

*nCmd*<br/>
指定要求的說明類型。 如需可能的值，以及它們如何影響*dwData*參數，請參閱[WinHelp](/windows/desktop/api/winuser/nf-winuser-winhelpa) Windows 函式。

### <a name="remarks"></a>備註

架構也會呼叫此函式來叫用 WinHelp 應用程式。

您的應用程式終止時，架構會自動關閉 WinHelp 應用程式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="writeprofilebinary"></a>  CWinApp::WriteProfileBinary

呼叫此成員函式，將二進位資料寫入至指定的區段的應用程式的登錄或。INI 檔案。

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
指向以 null 終止的字串，這個字串指定包含項目的區段。 如果區段不存在，它會建立它。 區段名稱是大小寫無關;字串可能會使用任何組合的大寫和小寫字母。

*lpszEntry*<br/>
指向以 null 結束的字串，其中包含的值是要寫入至其中的項目。 如果項目不存在於指定的區段中，它會建立它。

*pData*<br/>
要寫入的資料點。

*nBytes*<br/>
包含要寫入的位元組數目。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

這個範例會使用`CWinApp* pApp = AfxGetApp();`以取得說明的方式 CWinApp 類別所`WriteProfileBinary`和`GetProfileBinary`可從任何 MFC 應用程式中的函式。

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

如需其他範例，請參閱範例[CWinApp::GetProfileBinary](#getprofilebinary)。

##  <a name="writeprofileint"></a>  Cwinapp:: Writeprofileint

呼叫此成員函式，將指定的值寫入指定的區段的應用程式的登錄或。INI 檔案。

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
指向以 null 終止的字串，這個字串指定包含項目的區段。 如果區段不存在，它會建立它。 區段名稱是大小寫無關;字串可能會使用任何組合的大寫和小寫字母。

*lpszEntry*<br/>
指向以 null 結束的字串，其中包含的值是要寫入至其中的項目。 如果項目不存在於指定的區段中，它會建立它。

*n 值*<br/>
包含要寫入的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

這個範例會使用`CWinApp* pApp = AfxGetApp();`以取得說明的方式 CWinApp 類別所`WriteProfileString`， `WriteProfileInt`， `GetProfileString`，和`GetProfileInt`可從任何 MFC 應用程式中的函式。

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

如需其他範例，請參閱範例[CWinApp::GetProfileInt](#getprofileint)。

##  <a name="writeprofilestring"></a>  CWinApp::WriteProfileString

呼叫此成員函式，將指定的字串寫入應用程式的登錄的指定區段或。INI 檔案。

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>參數

*lpszSection*<br/>
指向以 null 終止的字串，這個字串指定包含項目的區段。 如果區段不存在，它會建立它。 區段名稱是大小寫無關;字串可能會使用任何組合的大寫和小寫字母。

*lpszEntry*<br/>
指向以 null 結束的字串，其中包含的值是要寫入至其中的項目。 如果項目不存在於指定的區段中，它會建立它。 如果此參數為 NULL 時，所指定的一節*lpszSection*會被刪除。

*lpszValue*<br/>
指向要寫入字串。 如果此參數為 NULL 時，所指定之項目的*lpszEntry*刪除參數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

如需其他範例，請參閱範例[CWinApp::GetProfileInt](#getprofileint)。

##  <a name="setappid"></a>  CWinApp::SetAppID

明確地設定應用程式的應用程式使用者模型識別碼。 任何使用者介面會呈現給使用者 （的最佳位置是應用程式建構函式） 之前，應該呼叫這個方法。

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>參數

*lpcszAppID*<br/>
指定應用程式使用者模型識別碼。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CWinThread 類別](../../mfc/reference/cwinthread-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[如何：新增重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)
