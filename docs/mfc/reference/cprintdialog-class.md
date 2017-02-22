---
title: "CPrintDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPrintDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintDialog class"
  - "列印對話方塊"
  - "Print Setup dialog box"
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CPrintDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 通用對話方塊中提供的服務進行列印。  
  
## 語法  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPrintDialog::CPrintDialog](../Topic/CPrintDialog::CPrintDialog.md)|建構 `CPrintDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPrintDialog::CreatePrinterDC](../Topic/CPrintDialog::CreatePrinterDC.md)|建立印表機內容，而不顯示列印對話方塊。|  
|[CPrintDialog::DoModal](../Topic/CPrintDialog::DoModal.md)|顯示  對話方塊可讓使用者進行選取。|  
|[CPrintDialog::GetCopies](../Topic/CPrintDialog::GetCopies.md)|擷取要求的複本數目。|  
|[CPrintDialog::GetDefaults](../Topic/CPrintDialog::GetDefaults.md)|擷取裝置預設值，而不顯示對話方塊。|  
|[CPrintDialog::GetDeviceName](../Topic/CPrintDialog::GetDeviceName.md)|擷取目前選取的印表機的名稱。|  
|[CPrintDialog::GetDevMode](../Topic/CPrintDialog::GetDevMode.md)|擷取 `DEVMODE` 結構。|  
|[CPrintDialog::GetDriverName](../Topic/CPrintDialog::GetDriverName.md)|擷取目前選取的印表機驅動程式的名稱。|  
|[CPrintDialog::GetFromPage](../Topic/CPrintDialog::GetFromPage.md)|擷取列印範圍的起始頁。|  
|[CPrintDialog::GetPortName](../Topic/CPrintDialog::GetPortName.md)|擷取目前選取的印表機通訊埠的名稱。|  
|[CPrintDialog::GetPrinterDC](../Topic/CPrintDialog::GetPrinterDC.md)|擷取控制代碼印表機內容。|  
|[CPrintDialog::GetToPage](../Topic/CPrintDialog::GetToPage.md)|擷取列印範圍的頁面。|  
|[CPrintDialog::PrintAll](../Topic/CPrintDialog::PrintAll.md)|判斷是否要列印文件的所有頁面。|  
|[CPrintDialog::PrintCollate](../Topic/CPrintDialog::PrintCollate.md)|判斷自動分頁的複本是否要求。|  
|[CPrintDialog::PrintRange](../Topic/CPrintDialog::PrintRange.md)|判斷是否要列印的頁面只能有一個指定的範圍。|  
|[CPrintDialog::PrintSelection](../Topic/CPrintDialog::PrintSelection.md)|判斷是否只列印目前選取的項目。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPrintDialog::m\_pd](../Topic/CPrintDialog::m_pd.md)|用於的結構 `CPrintDialog` 自訂物件。|  
  
## 備註  
 通用列印對話方塊讓您能夠輕鬆實作列印、列印設定對話方塊的部分符合 Windows 標準。  
  
> [!NOTE]
>  `CPrintDialogEx` 類別會封裝 Windows 2000 列印屬性工作表所提供的服務。  如需詳細資訊請參閱 [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) 概觀。  
  
 `CPrintDialog` 功能是由該 [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)替換，專為您提供通用對話方塊提供列印設定和版面設定。  
  
 您可以依賴這個架構處理列印的許多方面您應用程式的。  在這種情況下，架構會自動顯示列印的 Windows 通用對話方塊。  您也可以將應用程式的架構控制代碼列印，但是會覆寫具有自己的列印對話方塊的通用列印對話方塊。  如需使用架構的詳細資訊處理列印工作，請參閱本文 [列印](../../mfc/printing.md)。  
  
 如果您希望應用程式處理列印，沒有框架的相關狀態，您可以使用 `CPrintDialog` 類別所提供的建構函式，您也可以從 `CPrintDialog` 衍生自己的對話方塊類別和覆寫建構函式以配合您的需要。  在任何情況下，，因為它們從類別 `CCommonDialog`，取得這些對話方塊的行為會與標準 MFC 對話方塊。  
  
 使用 `CPrintDialog` 建構函式，才能使用 `CPrintDialog` 物件，請先建立物件。  一旦對話方塊所建構的，您可以設定或修改 [m\_pd](../Topic/CPrintDialog::m_pd.md) 結構中的所有值初始化對話方塊控制項的值。  `m_pd` 結構是型別 [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)。  如需此結構的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果您沒有提供您在 `m_pd` 的控制代碼 **hDevMode** 和 **hDevNames** 成員，請務必呼叫這些控制代碼的 Windows 函式 **GlobalFree** ，在完成對話方塊時。  當使用 `CWinApp::OnFilePrintSetup`時提供架構的列印設定實作，您就必須釋放這些控制代碼。  控制代碼是由 `CWinApp` 在 `CWinApp` 的解構函式 \(Destructor\) 維護和釋放。  當使用時，個別的 `CPrintDialog` 釋放這些控制代碼才是必要的。  
  
 在初始化對話方塊控制項後，請呼叫 `DoModal` 成員函式來顯示對話方塊並允許使用者選取列印選項。  `DoModal` 傳回使用者是否選取了決定 \(**IDOK**\) 或取消**IDCANCEL**\(\) 按鈕。  
  
 如果 `DoModal` 傳回 **IDOK**，您可以使用其中一個 `CPrintDialog` 的成員函式是由使用者輸入來擷取資訊。  
  
 `CPrintDialog::GetDefaults` 成員函式以擷取目前印表機預設很有用，而不顯示對話方塊。  這個成員函式不需要使用者互動。  
  
 您可以使用  視窗 **CommDlgExtendedError** 函式以判斷是否在  對話方塊中的初始化時發生錯誤以及了解錯誤。  如需這個函式的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `CPrintDialog` 仰賴隨附於 Windows 3.1 \(含\) 以後版本的 COMMDLG.DLL 檔案。  
  
 自訂對話方塊，請從 `CPrintDialog`衍生類別，以提供自訂對話方塊範本並將訊息對應的處理會從擴充的控制項傳回的通知訊息。  應該傳遞所有未處理訊息加入至基底類別。  攔截函式不需要自訂。  
  
 若要以不同方式處理相同的訊息會根據對話方塊是否為或列印、列印設定，您必須取得每個對話方塊的類別。  您也必須覆寫視窗 **AttachOnSetup** 函式，處理新的對話方塊的建立，當列印設定按鈕在 \[列印\] 對話方塊中選取 。  
  
 如需使用 `CPrintDialog`的資訊，請參閱 [通用對話方塊類別。](../../mfc/common-dialog-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [MFC 範例 DIBLOOK](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPrintInfo Structure](../../mfc/reference/cprintinfo-structure.md)