---
title: "CColorDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CColorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CColorDialog class"
  - "色彩, 對話方塊"
  - "對話方塊, 色彩"
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CColorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可讓您合併色彩選取對話方塊加入至您的應用程式。  
  
## 語法  
  
```  
class CColorDialog : public CCommonDialog  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CColorDialog::CColorDialog](../Topic/CColorDialog::CColorDialog.md)|建構 `CColorDialog` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CColorDialog::DoModal](../Topic/CColorDialog::DoModal.md)|顯示色彩對話方塊可讓使用者進行選取。|  
|[CColorDialog::GetColor](../Topic/CColorDialog::GetColor.md)|傳回包含選取色彩的值 **COLORREF** 結構。|  
|[CColorDialog::GetSavedCustomColors](../Topic/CColorDialog::GetSavedCustomColors.md)|擷取使用者所建立的自訂色彩。|  
|[CColorDialog::SetCurrentColor](../Topic/CColorDialog::SetCurrentColor.md)|強制目前色彩選取為指定的色彩。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CColorDialog::OnColorOK](../Topic/CColorDialog::OnColorOK.md)|驗證色彩的覆寫輸入至  對話方塊。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CColorDialog::m\_cc](../Topic/CColorDialog::m_cc.md)|用於的結構自訂對話方塊中的設定。|  
  
## 備註  
 `CColorDialog` 物件是用於顯示系統定義的色彩清單的對話方塊。  使用者可以從清單選取或建立特定色彩，然後會回報給應用程式，當對話方塊關閉時。  
  
 `CColorDialog` 建構物件，使用提供的建構函式或衍生新類別和使用自訂建構函式。  
  
 一旦對話方塊所建構的，您可以設定或修改[m\_cc](../Topic/CColorDialog::m_cc.md) 結構中的所有值初始化對話方塊控制項的值。  `m_cc` 結構是型別 [CHOOSECOLOR](http://msdn.microsoft.com/library/windows/desktop/ms646830)。  
  
 在初始化對話方塊的控制項後，請呼叫 `DoModal` 成員函式來顯示對話方塊並允許使用者選取色彩。  `DoModal` 傳回對話方塊的判斷**IDOK**\(\) 或 \(\)**IDCANCEL**取消按鈕的使用者選取的項目。  
  
 如果 `DoModal` 傳回 **IDOK**，您可以使用其中一個 `CColorDialog` 的成員函式是由使用者輸入來擷取資訊。  
  
 您可以使用  視窗 [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) 函式以判斷是否在  對話方塊中的初始化時發生錯誤以及了解錯誤。  
  
 `CColorDialog` 仰賴隨附於 Windows 3.1 \(含\) 以後版本的 COMMDLG.DLL 檔案。  
  
 自訂對話方塊，請從 `CColorDialog`衍生類別，以提供自訂對話方塊範本並將訊息對應的處理會從擴充的控制項傳回的通知訊息。  應將所有未處理訊息加入至基底類別。  
  
 攔截函式不需要自訂。  
  
> [!NOTE]
>  在某些安裝，如果您使用這種架構進行其他物件 `CDialog` 灰色， `CColorDialog` 物件不會以灰色背景顯示。  
  
 如需使用 `CColorDialog`的資訊，請參閱 [通用對話方塊類別。](../../mfc/common-dialog-classes.md)  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CColorDialog`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [MFC MDI 範例](../../top/visual-cpp-samples.md)   
 [MFC 範例 DRAWCLI](../../top/visual-cpp-samples.md)   
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)