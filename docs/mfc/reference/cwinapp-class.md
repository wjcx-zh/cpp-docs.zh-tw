---
title: "CWinApp Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinApp"
  - "hInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "application objects [C++]"
  - "CWinApp class"
  - "HINSTANCE"
  - "main object"
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CWinApp Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您會取得一個 Windows 應用程式物件的基底類別。  
  
## 語法  
  
```  
class CWinApp : public CWinThread  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWinApp::CWinApp](../Topic/CWinApp::CWinApp.md)|建構 `CWinApp` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinApp::AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)|將文件範本加入至可用的資料範本應用程式清單。|  
|[CWinApp::AddToRecentFileList](../Topic/CWinApp::AddToRecentFileList.md)|將檔案名稱加入至最近使用 \(MRU\) 的檔案清單。|  
|[CWinApp::ApplicationRecoveryCallback](../Topic/CWinApp::ApplicationRecoveryCallback.md)|呼叫由架構，在應用程式意外關閉。|  
|[CWinApp::CloseAllDocuments](../Topic/CWinApp::CloseAllDocuments.md)|關閉所有開啟的文件。|  
|[CWinApp::CreatePrinterDC](../Topic/CWinApp::CreatePrinterDC.md)|建立印表機內容。|  
|[CWinApp::DelRegTree](../Topic/CWinApp::DelRegTree.md)|刪除指定的機碼及其一切子機碼。|  
|[CWinApp::DoMessageBox](../Topic/CWinApp::DoMessageBox.md)|應用程式的實作 [AfxMessageBox](../Topic/AfxMessageBox.md) 。|  
|[CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md)|開啟和關閉等待游標。|  
|[CWinApp::EnableD2DSupport](../Topic/CWinApp::EnableD2DSupport.md)|啟用應用程式 `D2D` 支援。  初始化主視窗之前，呼叫這個方法。|  
|[CWinApp::EnableHtmlHelp](../Topic/CWinApp::EnableHtmlHelp.md)|應用程式的實作，而不是 HTMLHelp WinHelp。|  
|[CWinApp::EnableTaskbarInteraction](../Topic/CWinApp::EnableTaskbarInteraction.md)|啟用工作列互動。|  
|[CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md)|清除的覆寫，以便在應用程式結束。|  
|[CWinApp::GetApplicationRecoveryParameter](../Topic/CWinApp::GetApplicationRecoveryParameter.md)|擷取應用程式復原方法的輸入參數。|  
|[CWinApp::GetApplicationRecoveryPingInterval](../Topic/CWinApp::GetApplicationRecoveryPingInterval.md)|傳回重新啟動管理員等候復原回呼函式傳回的時間。|  
|[CWinApp::GetApplicationRestartFlags](../Topic/CWinApp::GetApplicationRestartFlags.md)|傳回重新啟動管理員的旗標。|  
|[CWinApp::GetAppRegistryKey](../Topic/CWinApp::GetAppRegistryKey.md)|以下的\\"Software"\\RegistryKey\\ProfileName RETURN 鍵。|  
|[CWinApp::GetDataRecoveryHandler](../Topic/CWinApp::GetDataRecoveryHandler.md)|取得應用程式的這個執行個體的資料復原管理員。|  
|[CWinApp::GetFirstDocTemplatePosition](../Topic/CWinApp::GetFirstDocTemplatePosition.md)|擷取第一個文件範本的位置。|  
|[CWinApp::GetHelpMode](../Topic/CWinApp::GetHelpMode.md)|擷取應用程式使用之說明的型別。|  
|[CWinApp::GetNextDocTemplate](../Topic/CWinApp::GetNextDocTemplate.md)|擷取文件範本的位置。  可以遞迴地使用。|  
|[CWinApp::GetPrinterDeviceDefaults](../Topic/CWinApp::GetPrinterDeviceDefaults.md)|擷取預設印表機。|  
|[CWinApp::GetProfileBinary](../Topic/CWinApp::GetProfileBinary.md)|從應用程式的 .INI 檔中的項目擷取二進位資料。|  
|[CWinApp::GetProfileInt](../Topic/CWinApp::GetProfileInt.md)|從應用程式的 .INI 檔中的項目擷取整數。|  
|[CWinApp::GetProfileString](../Topic/CWinApp::GetProfileString.md)|從應用程式的 .INI 檔中的項目擷取字串。|  
|[CWinApp::GetSectionKey](../Topic/CWinApp::GetSectionKey.md)|以下的\\"Software"\\RegistryKey\\AppName\\lpszSection RETURN 鍵。|  
|[CWinApp::HideApplication](../Topic/CWinApp::HideApplication.md)|在關閉文件之前隱藏應用程式。|  
|[CWinApp::HtmlHelp](../Topic/CWinApp::HtmlHelp.md)|`HTMLHelp` 呼叫 Windows 函式。|  
|[CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md)|執行 Windows 的覆寫執行個體初始化，例如建立自己的視窗物件。|  
|[CWinApp::IsTaskbarInteractionEnabled](../Topic/CWinApp::IsTaskbarInteractionEnabled.md)|告知 Windows 7 工作列互動是否啟用。|  
|[CWinApp::LoadCursor](../Topic/CWinApp::LoadCursor.md)|載入游標資源。|  
|[CWinApp::LoadIcon](../Topic/CWinApp::LoadIcon.md)|載入一個圖示資源。|  
|[CWinApp::LoadOEMCursor](../Topic/CWinApp::LoadOEMCursor.md)|載入 **OCR\_** 常數在 WINDOWS.H. 指定的視窗 OEM 預先定義的游標。|  
|[CWinApp::LoadOEMIcon](../Topic/CWinApp::LoadOEMIcon.md)|載入 **OIC\_** 常數在 WINDOWS.H. 指定的視窗 OEM 預先定義的圖示。|  
|[CWinApp::LoadStandardCursor](../Topic/CWinApp::LoadStandardCursor.md)|載入 **IDC\_** 常數在 WINDOWS.H. 指定的視窗預先定義的游標。|  
|[CWinApp::LoadStandardIcon](../Topic/CWinApp::LoadStandardIcon.md)|載入 **IDI\_** 常數在 WINDOWS.H. 指定的視窗預先定義的圖示。|  
|[CWinApp::OnDDECommand](../Topic/CWinApp::OnDDECommand.md)|呼叫框架以回應動態資料交換 \(DDE\) \(DDE\) 執行命令。|  
|[CWinApp::OnIdle](../Topic/CWinApp::OnIdle.md)|執行應用程式特有閒置時間處理的覆寫。|  
|[CWinApp::OpenDocumentFile](../Topic/CWinApp::OpenDocumentFile.md)|呼叫框架開啟檔案從檔案。|  
|[CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)|在命令列剖析個別參數和旗標。|  
|[CWinApp::PreTranslateMessage](../Topic/CWinApp::PreTranslateMessage.md)|篩選訊息，然後才會分派給 Windows 函式 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)之前。|  
|[CWinApp::ProcessMessageFilter](../Topic/CWinApp::ProcessMessageFilter.md)|攔截特定訊息，並在到達應用程式。|  
|[CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md)|處理命令列引數和旗標。|  
|[CWinApp::ProcessWndProcException](../Topic/CWinApp::ProcessWndProcException.md)|攔截應用程式的訊息和命令處理常式所擲回的所有未處理的例外狀況。|  
|[CWinApp::Register](../Topic/CWinApp::Register.md)|執行自訂記錄檔。|  
|[CWinApp::RegisterWithRestartManager](../Topic/CWinApp::RegisterWithRestartManager.md)|登錄使用重新啟動管理員的應用程式。|  
|[CWinApp::ReopenPreviousFilesAtRestart](../Topic/CWinApp::ReopenPreviousFilesAtRestart.md)|判斷重新啟動管理員是否重新開啟的檔案，在應用程式意外關閉。|  
|[CWinApp::RestartInstance](../Topic/CWinApp::RestartInstance.md)|處理序重新啟動管理員所啟始的重新啟動應用程式。|  
|[CWinApp::RestoreAutosavedFilesAtRestart](../Topic/CWinApp::RestoreAutosavedFilesAtRestart.md)|判斷重新啟動管理員是否要還原自動儲存的檔案，並重新啟動應用程式。|  
|[CWinApp::Run](../Topic/CWinApp::Run.md)|執行預設的訊息迴圈。  自訂訊息迴圈的覆寫。|  
|[CWinApp::RunAutomated](../Topic/CWinApp::RunAutomated.md)|提供 **\/Automation** 選取測試應用程式的命令列。  已過時。  相反地，請使用值。 [CCommandLineInfo::m\_bRunAutomated](../Topic/CCommandLineInfo::m_bRunAutomated.md) 在呼叫 [ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)之後。|  
|[CWinApp::RunEmbedded](../Topic/CWinApp::RunEmbedded.md)|提供 **\/Embedding** 選取測試應用程式的命令列。  已過時。  相反地，請使用值。 [CCommandLineInfo::m\_bRunEmbedded](../Topic/CCommandLineInfo::m_bRunEmbedded.md) 在呼叫 [ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)之後。|  
|[CWinApp::SaveAllModified](../Topic/CWinApp::SaveAllModified.md)|提示使用者儲存修改過的資料。|  
|[CWinApp::SelectPrinter](../Topic/CWinApp::SelectPrinter.md)|選取使用者先前運算式中的印表機可以列印對話方塊。|  
|[CWinApp::SetHelpMode](../Topic/CWinApp::SetHelpMode.md)|集合並初始化應用程式使用之說明的型別。|  
|[CWinApp::SupportsApplicationRecovery](../Topic/CWinApp::SupportsApplicationRecovery.md)|判斷重新啟動管理員是否復原非預期地結束應用程式。|  
|[CWinApp::SupportsAutosaveAtInterval](../Topic/CWinApp::SupportsAutosaveAtInterval.md)|判斷重新啟動管理員是否自動儲存開啟的文件在將組建排入佇列。|  
|[CWinApp::SupportsAutosaveAtRestart](../Topic/CWinApp::SupportsAutosaveAtRestart.md)|判斷重新啟動管理員是否自動儲存所有開啟的文件，在應用程式重新啟動。|  
|[CWinApp::SupportsRestartManager](../Topic/CWinApp::SupportsRestartManager.md)|判斷應用程式是否支援重新啟動管理員。|  
|[CWinApp::Unregister](../Topic/CWinApp::Unregister.md)|移除註冊所有已知由 `CWinApp` 物件註冊。|  
|[CWinApp::WinHelp](../Topic/CWinApp::WinHelp.md)|`WinHelp` 呼叫 Windows 函式。|  
|[CWinApp::WriteProfileBinary](../Topic/CWinApp::WriteProfileBinary.md)|將項目寫入二進位資料在應用程式中 .INI 檔。|  
|[CWinApp::WriteProfileInt](../Topic/CWinApp::WriteProfileInt.md)|將項目寫入整數在應用程式的 .INI 檔。|  
|[CWinApp::WriteProfileString](../Topic/CWinApp::WriteProfileString.md)|將輸入字串寫入應用程式的 .INI 檔。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinApp::EnableShellOpen](../Topic/CWinApp::EnableShellOpen.md)|允許使用者從開啟視窗檔案管理員的資料檔案。|  
|[CWinApp::LoadStdProfileSettings](../Topic/CWinApp::LoadStdProfileSettings.md)|載入標準 .INI 檔設定和啟用 MRU 檔案清單功能。|  
|[CWinApp::OnContextHelp](../Topic/CWinApp::OnContextHelp.md)|在應用程式中的控制代碼 SHIFT\+F1 說明。|  
|[CWinApp::OnFileNew](../Topic/CWinApp::OnFileNew.md)|實作 `ID_FILE_NEW` 命令。|  
|[CWinApp::OnFileOpen](../Topic/CWinApp::OnFileOpen.md)|實作 `ID_FILE_OPEN` 命令。|  
|[CWinApp::OnFilePrintSetup](../Topic/CWinApp::OnFilePrintSetup.md)|實作 `ID_FILE_PRINT_SETUP` 命令。|  
|[CWinApp::OnHelp](../Topic/CWinApp::OnHelp.md)|在應用程式中的控制代碼 F1 說明 \(使用目前的內容\)。|  
|[CWinApp::OnHelpFinder](../Topic/CWinApp::OnHelpFinder.md)|處理 `ID_HELP_FINDER` 和 `ID_DEFAULT_HELP` 命令。|  
|[CWinApp::OnHelpIndex](../Topic/CWinApp::OnHelpIndex.md)|處理 `ID_HELP_INDEX` 命令並提供預設的說明主題。|  
|[CWinApp::OnHelpUsing](../Topic/CWinApp::OnHelpUsing.md)|處理 `ID_HELP_USING` 命令。|  
|[CWinApp::RegisterShellFileTypes](../Topic/CWinApp::RegisterShellFileTypes.md)|註冊所有與 Windows 檔案管理員之應用程式的文件類型。|  
|[CWinApp::SetAppID](../Topic/CWinApp::SetAppID.md)|明確設定應用程式使用者應用程式模型的 ID。  應該呼叫這個方法，在所有使用者介面呈現給使用者之前 \(最佳位置是應用程式的建構函式\)。|  
|[CWinApp::SetRegistryKey](../Topic/CWinApp::SetRegistryKey.md)|在登錄中建立應用程式設定儲存而非 .INI 檔。|  
|[CWinApp::UnregisterShellFileTypes](../Topic/CWinApp::UnregisterShellFileTypes.md)|移除註冊所有與 Windows 檔案管理員之應用程式的文件類型。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWinApp::m\_bHelpMode](../Topic/CWinApp::m_bHelpMode.md)|表示使用者是否在說明內容模式 \(通常會叫用 \(Invoke\) SHIFT\+F1\)。|  
|[CWinApp::m\_eHelpType](../Topic/CWinApp::m_eHelpType.md)|指定應用程式使用之說明的型別。|  
|[CWinApp::m\_hInstance](../Topic/CWinApp::m_hInstance.md)|識別應用程式的目前執行個體。|  
|[CWinApp::m\_lpCmdLine](../Topic/CWinApp::m_lpCmdLine.md)|為應用程式指定命令列的 NULL 結尾字串的點。|  
|[CWinApp::m\_nCmdShow](../Topic/CWinApp::m_nCmdShow.md)|指定視窗如何一開始會顯示。|  
|[CWinApp::m\_pActiveWnd](../Topic/CWinApp::m_pActiveWnd.md)|指標容器應用程式的主視窗，當一個 OLE 伺服器是就地啟動。|  
|[CWinApp::m\_pszAppID](../Topic/CWinApp::m_pszAppID.md)|應用程式模型使用者 ID.|  
|[CWinApp::m\_pszAppName](../Topic/CWinApp::m_pszAppName.md)|指定應用程式的名稱。|  
|[CWinApp::m\_pszExeName](../Topic/CWinApp::m_pszExeName.md)|應用程式的模組名稱。|  
|[CWinApp::m\_pszHelpFilePath](../Topic/CWinApp::m_pszHelpFilePath.md)|應用程式的說明檔的路徑。|  
|[CWinApp::m\_pszProfileName](../Topic/CWinApp::m_pszProfileName.md)|應用程式的 .INI 檔名。|  
|[CWinApp::m\_pszRegistryKey](../Topic/CWinApp::m_pszRegistryKey.md)|用來判斷儲存應用程式設定檔設定完整登錄機碼。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWinApp::m\_dwRestartManagerSupportFlags](../Topic/CWinApp::m_dwRestartManagerSupportFlags.md)|旗標判斷重新啟動管理員的行為方式。|  
|[CWinApp::m\_nAutosaveInterval](../Topic/CWinApp::m_nAutosaveInterval.md)|時間之間的毫秒自動儲存。|  
|[CWinApp::m\_pDataRecoveryHandler](../Topic/CWinApp::m_pDataRecoveryHandler.md)|對資料復原管理員的指標應用程式的。|  
  
## 備註  
 應用程式物件的成員函式以初始化應用程式 \(和每個執行個體\) 以及執行應用程式。  
  
 使用 Microsoft Foundation Class 的每個應用程式只能包含 `CWinApp`從衍生的物件。  這會建構物件，而其他 C\+\+ 全域建構物件時已經存在，便可以使用  視窗 `WinMain` 呼叫函式時， MFC 程式庫提供。  宣告您的衍生 `CWinApp` 物件在全域層級。  
  
 當您從 `CWinApp`衍生時應用程式類別，請覆寫 [InitInstance](../Topic/CWinApp::InitInstance.md) 成員函式來建置應用程式的主視窗物件。  
  
 除了 `CWinApp` 成員函式之外， MFC 程式庫提供下列全域函式存取您的 `CWinApp` 物件和其他全域資訊:  
  
-   [AfxGetApp](../Topic/AfxGetApp.md) 取得指標 `CWinApp` 物件。  
  
-   [AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md) 取得的控制代碼目前應用程式執行個體。  
  
-   [AfxGetResourceHandle](../Topic/AfxGetResourceHandle.md) 取得的控制代碼傳遞給應用程式的資源。  
  
-   [AfxGetAppName](../Topic/AfxGetAppName.md) 衍生的指標會包含應用程式名稱的字串。  此外，因此，如果您有一個指標 `CWinApp` 物件，請使用 `m_pszExeName` 取得應用程式名稱。  
  
 如需更多參閱 [CWinApp:應用程式類別](../../mfc/cwinapp-the-application-class.md) 在 `CWinApp` 類別的概觀，包括下列:  
  
-   `CWinApp`\-應用程式精靈所撰寫的衍生的程式碼。  
  
-   在應用程式執行順序的 `CWinApp` 的效果。  
  
-   `CWinApp` 的預設成員函式的實作。  
  
-   `CWinApp` 的金鑰 overridables。  
  
 **m\_hPrevInstance** 資料成員不存在。  如需偵測 `CWinApp`前一個執行個體的詳細資訊，請參閱知識庫文件\<如何識別應用程式的前一個執行個體」\(KB106385\) 中 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;106385](http://support.microsoft.com/default.aspx?scid=kb;en-us;106385)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CWinThread Class](../../mfc/reference/cwinthread-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [如何：加入重新啟動管理員支援](../../mfc/how-to-add-restart-manager-support.md)