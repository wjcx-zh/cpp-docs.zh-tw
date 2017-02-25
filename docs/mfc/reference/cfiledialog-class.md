---
title: "CFileDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileDialog class"
  - "common file dialog boxes"
  - "對話方塊, common"
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: 47
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 49
---
# CFileDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝為檔案使用開啟或檔案儲存作業的通用對話方塊。  
  
## 語法  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)|建構 `CFileDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileDialog::AddCheckButton](../Topic/CFileDialog::AddCheckButton.md)|將檢查按鈕加入至對話方塊。|  
|[CFileDialog::AddComboBox](../Topic/CFileDialog::AddComboBox.md)|將下拉式方塊加入至對話方塊。|  
|[CFileDialog::AddControlItem](../Topic/CFileDialog::AddControlItem.md)|將項目加入至對話方塊的容器控制項。|  
|[CFileDialog::AddEditBox](../Topic/CFileDialog::AddEditBox.md)|將編輯方塊到對話方塊。|  
|[CFileDialog::AddMenu](../Topic/CFileDialog::AddMenu.md)|將功能表加入至對話方塊。|  
|[CFileDialog::AddPlace](../Topic/CFileDialog::AddPlace.md)|多載。  將資料夾加入位置的清單可供使用者可以開啟或儲存項目。|  
|[CFileDialog::AddPushButton](../Topic/CFileDialog::AddPushButton.md)|將按鈕加入至對話方塊。|  
|[CFileDialog::AddRadioButtonList](../Topic/CFileDialog::AddRadioButtonList.md)|將選項按鈕 \(也稱為選項按鈕群組加入至對話方塊。|  
|[CFileDialog::AddSeparator](../Topic/CFileDialog::AddSeparator.md)|加入分隔符號加入至對話方塊。|  
|[CFileDialog::AddText](../Topic/CFileDialog::AddText.md)|將文字內容到對話方塊。|  
|[CFileDialog::ApplyOFNToShellDialog](../Topic/CFileDialog::ApplyOFNToShellDialog.md)|更新 `CFileDialog` 狀態符合 `m_ofn` 成員變數和旗標儲存的參數。|  
|[CFileDialog::DoModal](../Topic/CFileDialog::DoModal.md)|顯示對話方塊並讓使用者進行選取。|  
|[CFileDialog::EnableOpenDropDown](../Topic/CFileDialog::EnableOpenDropDown.md)|啟用 \[**開啟**\] 或 \[**儲存**\] 按鈕的下拉式清單在對話方塊。|  
|[CFileDialog::EndVisualGroup](../Topic/CFileDialog::EndVisualGroup.md)|停止項目加入至對話方塊的視覺化群組。|  
|[CFileDialog::GetCheckButtonState](../Topic/CFileDialog::GetCheckButtonState.md)|取得一個檢查按鈕 \(核取方塊\) 的目前狀態在對話方塊。|  
|[CFileDialog::GetControlItemState](../Topic/CFileDialog::GetControlItemState.md)|取得項目的目前狀態對話方塊中找到的容器控制項的。|  
|[CFileDialog::GetControlState](../Topic/CFileDialog::GetControlState.md)|取得指定之控制項的目前可見且已啟用狀態。|  
|[CFileDialog::GetEditBoxText](../Topic/CFileDialog::GetEditBoxText.md)|取得在編輯方塊控制項的目前文字。|  
|[CFileDialog::GetFileExt](../Topic/CFileDialog::GetFileExt.md)|傳回選取之檔案的副檔名。|  
|[CFileDialog::GetFileName](../Topic/CFileDialog::GetFileName.md)|傳回所選取檔案的檔案名稱。|  
|[CFileDialog::GetFileTitle](../Topic/CFileDialog::GetFileTitle.md)|傳回所選取檔案的標題。|  
|[CFileDialog::GetFolderPath](../Topic/CFileDialog::GetFolderPath.md)|擷取目前開啟的資料夾或目錄之路徑的檔案總管樣式 \[**開啟**\] 或 \[**另存新檔**\] 通用對話方塊的。|  
|[CFileDialog::GetIFileDialogCustomize](../Topic/CFileDialog::GetIFileDialogCustomize.md)|擷取自訂的 `CFileDialog` 物件內部 COM 物件。|  
|[CFileDialog::GetIFileOpenDialog](../Topic/CFileDialog::GetIFileOpenDialog.md)|擷取做為 \[**開啟**\] 檔案對話方塊 `CFileDialog` 內使用 COM 物件。|  
|[CFileDialog::GetIFileSaveDialog](../Topic/CFileDialog::GetIFileSaveDialog.md)|擷取做為 \[**儲存**\] 檔案對話方塊 `CFileDialog` 內使用 COM 物件。|  
|[CFileDialog::GetNextPathName](../Topic/CFileDialog::GetNextPathName.md)|傳回接下來選取之檔案的完整路徑。|  
|[CFileDialog::GetOFN](../Topic/CFileDialog::GetOFN.md)|擷取 `CFileDialog` 物件的 `OPENFILENAME` 結構。|  
|[CFileDialog::GetPathName](../Topic/CFileDialog::GetPathName.md)|傳回選取之檔案的完整路徑。|  
|[CFileDialog::GetReadOnlyPref](../Topic/CFileDialog::GetReadOnlyPref.md)|傳回選取之檔案的唯讀狀態。|  
|[CFileDialog::GetResult](../Topic/CFileDialog::GetResult.md)|取得使用者在對話所做的選擇。|  
|[CFileDialog::GetResults](../Topic/CFileDialog::GetResults.md)|取得允許多重選取的對話方塊的使用者的選擇。|  
|[CFileDialog::GetSelectedControlItem](../Topic/CFileDialog::GetSelectedControlItem.md)|從對話方塊中指定的容器控制項取得的特定項目。|  
|[CFileDialog::GetStartPosition](../Topic/CFileDialog::GetStartPosition.md)|傳回清單中第一個項目的位置。|  
|[CFileDialog::HideControl](../Topic/CFileDialog::HideControl.md)|隱藏了檔案總管樣式 \[**開啟**\] 或 \[**另存新檔**\] 通用對話方塊中指定的控制項。|  
|[CFileDialog::IsPickFoldersMode](../Topic/CFileDialog::IsPickFoldersMode.md)|是否在資料夾選擇器模式判斷目前對話方塊。|  
|[CFileDialog::MakeProminent](../Topic/CFileDialog::MakeProminent.md)|在對話方塊中放置控制項，以便與其他站立加入的控制項相比較。|  
|[CFileDialog::RemoveControlItem](../Topic/CFileDialog::RemoveControlItem.md)|從對話方塊的容器控制項中移除項目。|  
|[CFileDialog::SetCheckButtonState](../Topic/CFileDialog::SetCheckButtonState.md)|設定一個檢查按鈕 \(核取方塊\) 的目前狀態在對話方塊。|  
|[CFileDialog::SetControlItemState](../Topic/CFileDialog::SetControlItemState.md)|設定項目的目前狀態對話方塊中找到的容器控制項的。|  
|[CFileDialog::SetControlItemText](../Topic/CFileDialog::SetControlItemText.md)|設定控制項中的文字。  例如，隨附一個選項按鈕或項目在功能表上的文字。|  
|[CFileDialog::SetControlLabel](../Topic/CFileDialog::SetControlLabel.md)|設定文字與控制項，例如按鈕、文字或編輯方塊標籤。|  
|[CFileDialog::SetControlState](../Topic/CFileDialog::SetControlState.md)|設定指定之控制項的目前可見且已啟用狀態。|  
|[CFileDialog::SetControlText](../Topic/CFileDialog::SetControlText.md)|設定指定控制項的文字就會檔案總管樣式 \[**開啟** \] 或 \[**另存新檔**\] 通用對話方塊。|  
|[CFileDialog::SetDefExt](../Topic/CFileDialog::SetDefExt.md)|將檔案總管樣式 \[**開啟**\] 或 \[**另存新檔**\] 通用對話方塊的預設副檔名。|  
|[CFileDialog::SetEditBoxText](../Topic/CFileDialog::SetEditBoxText.md)|設定在編輯方塊控制項的目前文字。|  
|[CFileDialog::SetProperties](../Topic/CFileDialog::SetProperties.md)|提供定義為項目所使用的預設值所儲存的一個屬性存放區。|  
|[CFileDialog::SetSelectedControlItem](../Topic/CFileDialog::SetSelectedControlItem.md)|在選項按鈕群組中設定特定項目的選取狀態或下拉式方塊中的對話方塊中的。|  
|[CFileDialog::SetTemplate](../Topic/CFileDialog::SetTemplate.md)|設定物件的 `CFileDialog` 對話方塊範本。|  
|[CFileDialog::StartVisualGroup](../Topic/CFileDialog::StartVisualGroup.md)|宣告對話方塊的視覺化群組。  任何後續的「加入」方法將這些項目加入至此群組。|  
|[CFileDialog::UpdateOFNFromShellDialog](../Topic/CFileDialog::UpdateOFNFromShellDialog.md)|更新在 `m_ofn` 成員變數儲存的資料符合檔案對話方塊的目前狀態。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileDialog::OnButtonClicked](../Topic/CFileDialog::OnButtonClicked.md)|呼叫，當按一下按鈕。|  
|[CFileDialog::OnCheckButtonToggled](../Topic/CFileDialog::OnCheckButtonToggled.md)|呼叫時，核取方塊已核取、未核取。|  
|[CFileDialog::OnControlActivating](../Topic/CFileDialog::OnControlActivating.md)|呼叫，當控制項正在使用中的。|  
|[CFileDialog::OnFileNameChange](../Topic/CFileDialog::OnFileNameChange.md)|處理 `WM_NOTIFY CDN_SELCHANGE` 訊息。|  
|[CFileDialog::OnFileNameOK](../Topic/CFileDialog::OnFileNameOK.md)|驗證在對話方塊中輸入的檔案名稱。|  
|[CFileDialog::OnFolderChange](../Topic/CFileDialog::OnFolderChange.md)|處理 `WM_NOTIFY CDN_FOLDERCHANGE` 訊息。|  
|[CFileDialog::OnInitDone](../Topic/CFileDialog::OnInitDone.md)|處理 `WM_NOTIFY CDN_INITDONE` 訊息。|  
|[CFileDialog::OnItemSelected](../Topic/CFileDialog::OnItemSelected.md)|呼叫時，容器項目已選取。|  
|[CFileDialog::OnLBSelChangedNotify](../Topic/CFileDialog::OnLBSelChangedNotify.md)|檔案時，選取範圍變更時，可讓您執行自訂動作。|  
|[CFileDialog::OnShareViolation](../Topic/CFileDialog::OnShareViolation.md)|控制代碼共用違規。|  
|[CFileDialog::OnTypeChange](../Topic/CFileDialog::OnTypeChange.md)|處理 `WM_NOTIFY CDN_TYPECHANGE` 訊息。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFileDialog::m\_ofn](../Topic/CFileDialog::m_ofn.md)|視窗 `OPENFILENAME` 結構。  提供對基本檔案對話方塊參數。|  
  
## 備註  
 通用檔案對話方塊讓與 Windows 標準一致您實作檔案選取對話方塊，例如， \[**開啟檔案**\] 和 \[**另存新檔**\]，有些。  
  
 您可以使用 [CFileDialog](../../mfc/reference/cfiledialog-class.md) 與提供的建構函式，也可以從 `CFileDialog` 衍生自己的對話方塊類別和覆寫建構函式以配合您的需要。  在任何情況下，，因為它們從 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)，取得這些對話方塊的行為會與標準 MFC 對話方塊。  `CFileDialog` 相依於視窗中包含的 COMMDLG.DLL 檔案。  
  
 外觀和 `CFileDialog` 的功能和 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 視窗與舊版不同。  如果程式編譯並在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下，執行預設 `CFileDialog` 自動使用新的 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 模式，而沒有程式碼變更。  使用 `bVistaStyle` 參數在建構函式中手動覆寫此自動更新。  對自動更新的例外狀況是自訂的對話方塊。  它們不會轉換成新的樣式。  如需建構函式的詳細資訊，請參閱 [CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)。  
  
> [!NOTE]
>  因此，使用 `CFileDialog`時，控制項 ID 系統在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 不同與舊版 Windows。  才能移植從視窗之前，舊版的專案必須更新 `CFileDialog` 對控制項的所有參考程式碼。  
  
 陣列 `CFileDialog` 方法不支援在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下。  檢查個別方法主題有關的資訊是否支援方法。  此外，下列繼承的函式不支援在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下:  
  
-   [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)  
  
-   [CDialog::OnSetFont](../Topic/CDialog::OnSetFont.md)  
  
 `CFileDialog` 類別的 Windows 訊息隨著所需的作業系統而定。  例如， Windows XP 不支援 [CDialog::OnCancel](../Topic/CDialog::OnCancel.md) 和 [CDialog::OnOK](../Topic/CDialog::OnOK.md)`CFileDialog` 類別的。  不過， [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 支援它們。  如需產生和命令它們的不同接收訊息的詳細資訊，請參閱 [CFileDialog 範例:記錄事件順序](../../top/visual-cpp-samples.md)。  
  
 使用 `CFileDialog` 建構函式，要使用 `CFileDialog` 物件，請先建立物件。  在對話方塊中建構之後，您可以設定或修改 [CFileDialog::m\_ofn](../Topic/CFileDialog::m_ofn.md) 結構的所有值初始化對話方塊控制項的值或狀態。  `m_ofn` 結構是型別 `OPENFILENAME`。  如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)][OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839) 結構。  
  
 在您使用對話方塊控制項後，請呼叫 [CFileDialog::DoModal](../Topic/CFileDialog::DoModal.md) 方法會顯示對話方塊，讓使用者可以輸入路徑和檔名。  `DoModal` 傳回使用者是否按下判斷 \(IDOK\) 或取消 IDCANCEL \(\) 按鈕。  如果 `DoModal` IDOK 傳回，您可以使用其中一 `CFileDialog` 公用成員函式以取得使用者投入的資訊。  
  
> [!NOTE]
>  在 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]下，對 [IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980) 的多個呼叫會造成錯誤。  對 `SetFileTypes` 的第二個呼叫 `CFileDialog` 的所有執行個體將會傳回 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]的 `E_UNEXPECTED` 。  某些方法 `CFileDialog` 函式呼叫 `SetFileTypes`。  例如，對 `CFileDialog::DoModal` 兩次呼叫 `CFileDialog` 的同一個執行個體產生 [判斷提示](../Topic/ASSERT%20\(MFC\).md)。  
  
 `CFileDialog` 包括可讓您執行自訂處理共用違規、檔名驗證和清單方塊變更告知的幾個受保護的成員。  這些受保護成員是回呼函式大部分應用程式不需要使用，因為預設處理自動執行。  這些函式的訊息對應項目，因為它們是標準虛擬函式，就不需要。  
  
 您可以使用視窗 [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) 函式判斷是否在對話方塊的初始設定期間發生和了解錯誤。  
  
 `CFileDialog` 物件的解構自動處理。  您不需要呼叫 [CDialog::EndDialog](../Topic/CDialog::EndDialog.md)。  
  
 在呼叫 `DoModal`前，要讓使用者選取多個檔案，請將 `OFN_ALLOWMULTISELECT` 旗標。  您必須自行提供的檔案名稱緩衝區容納多檔案名稱傳回的清單。  透過取代 `m_ofn.lpstrFile` 利用指標對您已配置的緩衝區，，在建構之後， `CFileDialog`，但是，在您呼叫之前 `DoModal`。  
  
 此外，您必須設定 `m_ofn.nMaxFile` 使用字元數緩衝區指向 `m_ofn.lpstrFile`。  如果您設定要選取之檔案的最大數目。 `n`，所需的緩衝區大小。 `n * (_MAX_PATH + 1) + 1`。  在緩衝區所傳回的第一個項目是路徑檔案中選取的資料夾。  對於 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]式對話方塊中，目錄和檔案名稱字串以 null 結束，具有額外 null 字元在最後一個檔案名稱之後。  這個格式使檔案總管樣式的對話方塊會傳回包含空格的長檔名。  對於舊式對話方塊，目錄和檔案名稱字串以空格分隔，而函式為有空白的檔名使用短檔名。  
  
 下列範例示範如何使用緩衝區擷取和列出多個檔案名稱。  
  
 [!code-cpp[NVC_MFCFiles#23](../../mfc/codesnippet/CPP/cfiledialog-class_1.cpp)]  
  
 若要變更緩衝區大小以回應選取多個檔案名稱的使用者，您必須從 `CFileDialog` 衍生新的類別並覆寫方法 [CFileDialog::OnFileNameChange](../Topic/CFileDialog::OnFileNameChange.md) 。  
  
 如果您從 `CFileDialog`衍生新類別，您可以使用訊息對應處理所有訊息。  若要擴充預設訊息處理， `CFileDialog`從衍生類別，將訊息對應到新的類別，並為新訊息提供成員函式。  您不需要提供攔截函式自訂對話方塊。  
  
 自訂對話方塊，從 `CFileDialog`衍生類別，提供自訂對話方塊範本並加入訊息對應的處理會從擴充控制項的通知訊息。  將所有原始訊息的基底類別。  您不需要自訂攔截函式。  
  
 當您使用 `CFileDialog`的 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 樣式時，您無法使用訊息對應和對話方塊範本。  相反地，您必須提供類似的功能使用 COM 介面。  
  
 如需如何使用 `CFileDialog`的詳細資訊，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## 需求  
 **標題:** afxdlgs.h  
  
## 請參閱  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)