---
title: "CPrintDialogEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPrintDialogEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintDialogEx class"
  - "列印對話方塊"
  - "Print Setup dialog box"
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrintDialogEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 2000 列印屬性工作表所提供的服務。  
  
## 語法  
  
```  
class CPrintDialogEx : public CCommonDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPrintDialogEx::CPrintDialogEx](../Topic/CPrintDialogEx::CPrintDialogEx.md)|建構 `CPrintDialogEx` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPrintDialogEx::CreatePrinterDC](../Topic/CPrintDialogEx::CreatePrinterDC.md)|建立印表機內容，而不顯示列印對話方塊。|  
|[CPrintDialogEx::DoModal](../Topic/CPrintDialogEx::DoModal.md)|顯示  對話方塊可讓使用者進行選取。|  
|[CPrintDialogEx::GetCopies](../Topic/CPrintDialogEx::GetCopies.md)|擷取要求的複本數目。|  
|[CPrintDialogEx::GetDefaults](../Topic/CPrintDialogEx::GetDefaults.md)|擷取裝置預設值，而不顯示對話方塊。|  
|[CPrintDialogEx::GetDeviceName](../Topic/CPrintDialogEx::GetDeviceName.md)|擷取目前選取的印表機的名稱。|  
|[CPrintDialogEx::GetDevMode](../Topic/CPrintDialogEx::GetDevMode.md)|擷取 `DEVMODE` 結構。|  
|[CPrintDialogEx::GetDriverName](../Topic/CPrintDialogEx::GetDriverName.md)|擷取系統定義的印表機裝置驅動程式的名稱。|  
|[CPrintDialogEx::GetPortName](../Topic/CPrintDialogEx::GetPortName.md)|擷取目前選取的印表機通訊埠的名稱。|  
|[CPrintDialogEx::GetPrinterDC](../Topic/CPrintDialogEx::GetPrinterDC.md)|擷取控制代碼印表機內容。|  
|[CPrintDialogEx::PrintAll](../Topic/CPrintDialogEx::PrintAll.md)|判斷是否要列印文件的所有頁面。|  
|[CPrintDialogEx::PrintCollate](../Topic/CPrintDialogEx::PrintCollate.md)|判斷自動分頁的複本是否要求。|  
|[CPrintDialogEx::PrintCurrentPage](../Topic/CPrintDialogEx::PrintCurrentPage.md)|判斷是否要列印文件的目前頁面。|  
|[CPrintDialogEx::PrintRange](../Topic/CPrintDialogEx::PrintRange.md)|判斷是否要列印的頁面只能有一個指定的範圍。|  
|[CPrintDialogEx::PrintSelection](../Topic/CPrintDialogEx::PrintSelection.md)|判斷是否只列印目前選取的項目。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPrintDialogEx::m\_pdex](../Topic/CPrintDialogEx::m_pdex.md)|用於的結構 `CPrintDialogEx` 自訂物件。|  
  
## 備註  
 您可以依賴這個架構處理列印的許多方面您應用程式的。  如需使用架構的詳細資訊處理列印工作，請參閱本文 [列印](../../mfc/printing.md)。  
  
 如果您希望應用程式處理列印，沒有框架的相關狀態，您可以使用 `CPrintDialogEx` 類別所提供的建構函式，您也可以從 `CPrintDialogEx` 衍生自己的對話方塊類別和覆寫建構函式以配合您的需要。  在任何情況下，，因為它們從類別 `CCommonDialog`，取得這些對話方塊的行為會與標準 MFC 對話方塊。  
  
 使用 `CPrintDialogEx` 建構函式，才能使用 `CPrintDialogEx` 物件，請先建立物件。  一旦對話方塊所建構的，您可以設定或修改 [m\_pdex](../Topic/CPrintDialogEx::m_pdex.md) 結構中的所有值初始化對話方塊控制項的值。  `m_pdex` 結構是型別 [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)。  如需此結構的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如果您沒有提供您在 `m_pdex` 的控制代碼 **hDevMode** 和 **hDevNames** 成員，請務必呼叫這些控制代碼的 Windows 函式 **GlobalFree** ，在完成對話方塊時。  
  
 在初始化對話方塊控制項後，請呼叫 `DoModal` 成員函式來顯示對話方塊並允許使用者選取列印選項。  當 `DoModal` 傳回時，您可以判斷使用者是否選取了，以判斷應用程式或取消按鈕。  
  
 如果使用者按下決定，您可以使用 `CPrintDialogEx` 的成員函式是由使用者輸入來擷取資訊。  
  
 `CPrintDialogEx::GetDefaults` 成員函式以擷取目前印表機預設很有用，而不顯示對話方塊。  這個方法不需要使用者互動。  
  
 您可以使用  視窗 **CommDlgExtendedError** 函式以判斷是否在  對話方塊中的初始化時發生錯誤以及了解錯誤。  如需這個函式的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需使用 `CPrintDialogEx`的資訊，請參閱 [通用對話方塊類別。](../../mfc/common-dialog-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `IObjectWithSite`  
  
 `IPrintDialogCallback`  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialogEx`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPrintInfo Structure](../../mfc/reference/cprintinfo-structure.md)