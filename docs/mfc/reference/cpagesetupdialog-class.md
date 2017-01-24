---
title: "CPageSetupDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPageSetupDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPageSetupDialog class"
  - "OLE Page Setup dialog box"
  - "網頁設定"
  - "版面設定對話方塊"
  - "Print Setup dialog box"
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPageSetupDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Windows 通用 OLE 版面設定對話方塊中提供的服務附加支援設定及修改列印框線。  
  
## 語法  
  
```  
class CPageSetupDialog : public CCommonDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPageSetupDialog::CPageSetupDialog](../Topic/CPageSetupDialog::CPageSetupDialog.md)|建構 `CPageSetupDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPageSetupDialog::CreatePrinterDC](../Topic/CPageSetupDialog::CreatePrinterDC.md)|建立列印的裝置內容。|  
|[CPageSetupDialog::DoModal](../Topic/CPageSetupDialog::DoModal.md)|顯示  對話方塊可讓使用者進行選取。|  
|[CPageSetupDialog::GetDeviceName](../Topic/CPageSetupDialog::GetDeviceName.md)|傳回印表機的裝置名稱。|  
|[CPageSetupDialog::GetDevMode](../Topic/CPageSetupDialog::GetDevMode.md)|傳回印表機的目前 `DEVMODE` 。|  
|[CPageSetupDialog::GetDriverName](../Topic/CPageSetupDialog::GetDriverName.md)|傳回印表機使用的驅動程式。|  
|[CPageSetupDialog::GetMargins](../Topic/CPageSetupDialog::GetMargins.md)|傳回印表機的目前邊界設定。|  
|[CPageSetupDialog::GetPaperSize](../Topic/CPageSetupDialog::GetPaperSize.md)|傳回印表機的紙張大小。|  
|[CPageSetupDialog::GetPortName](../Topic/CPageSetupDialog::GetPortName.md)|傳回輸出連接埠名稱。|  
|[CPageSetupDialog::OnDrawPage](../Topic/CPageSetupDialog::OnDrawPage.md)|呼叫由架構所呈現列印頁面的畫面影像。|  
|[CPageSetupDialog::PreDrawPage](../Topic/CPageSetupDialog::PreDrawPage.md)|呼叫堆疊中呈現列印頁面的畫面影像之前。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPageSetupDialog::m\_psd](../Topic/CPageSetupDialog::m_psd.md)|用於的結構 `CPageSetupDialog` 自訂物件。|  
  
## 備註  
 這個類別是設計來取代列印設定對話方塊。  
  
 使用 `CPageSetupDialog` 建構函式，才能使用 `CPageSetupDialog` 物件，請先建立物件。  一旦對話方塊所建構的，您可以設定或修改 `m_psd` 資料成員的所有值初始化對話方塊控制項的值。  [m\_psd](../Topic/CPageSetupDialog::m_psd.md) 結構是型別 **PAGESETUPDLG**。  
  
 在初始化對話方塊控制項後，請呼叫 `DoModal` 成員函式來顯示對話方塊並允許使用者選取列印選項。  `DoModal` 傳回使用者是否選取了決定 \(**IDOK**\) 或取消**IDCANCEL**\(\) 按鈕。  
  
 如果 `DoModal` 傳回 **IDOK**，您可以使用的 `CPageSetupDialog` 的成員函式，或是存取 `m_psd` 資料成員，讓使用者擷取資訊項目。  
  
> [!NOTE]
>  在通用 OLE 版面設定\] 對話方塊隨即關閉之後，使用者所做的任何變更都不會由架構來儲存。  它是由應用程式決定儲存這個對話方塊儲存任何值至永久位置，例如應用程式的文件或應用程式類別的成員。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [MFC 範例 WORDPAD](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)