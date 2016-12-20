---
title: "CMFCColorDialog Class | Microsoft Docs"
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
  - "CMFCColorDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorDialog class"
  - "CMFCColorDialog::m_bIsMyPalette data member"
  - "CMFCColorDialog::m_bPickerMode data member"
  - "CMFCColorDialog::m_btnColorSelect data member"
  - "CMFCColorDialog::m_CurrentColor data member"
  - "CMFCColorDialog::m_hcurPicker data member"
  - "CMFCColorDialog::m_NewColor data member"
  - "CMFCColorDialog::m_pColourSheetOne data member"
  - "CMFCColorDialog::m_pColourSheetTwo data member"
  - "CMFCColorDialog::m_pPalette data member"
  - "CMFCColorDialog::m_pPropSheet data member"
  - "CMFCColorDialog::m_wndColors data member"
  - "CMFCColorDialog::m_wndStaticPlaceHolder data member"
  - "CMFCColorDialog::PreTranslateMessage method"
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorDialog` 類別表示色彩選取對話方塊。  
  
## 語法  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorDialog::CMFCColorDialog](../Topic/CMFCColorDialog::CMFCColorDialog.md)|建構 `CMFCColorDialog` 物件。|  
|`CMFCColorDialog::~CMFCColorDialog`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorDialog::GetColor](../Topic/CMFCColorDialog::GetColor.md)|傳回目前所選取的色彩。|  
|[CMFCColorDialog::GetPalette](../Topic/CMFCColorDialog::GetPalette.md)|傳回色板。|  
|`CMFCColorDialog::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  如需語法的詳細資訊，請參閱 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。  \(覆寫 `CDialogEx::PreTranslateMessage`\)。|  
|[CMFCColorDialog::RebuildPalette](../Topic/CMFCColorDialog::RebuildPalette.md)|從系統調色盤衍生出一個調色盤。|  
|[CMFCColorDialog::SetCurrentColor](../Topic/CMFCColorDialog::SetCurrentColor.md)|設定目前所選取的色彩。|  
|[CMFCColorDialog::SetNewColor](../Topic/CMFCColorDialog::SetNewColor.md)|設定色彩最相當於指定的 RGB 值。|  
|[CMFCColorDialog::SetPageOne](../Topic/CMFCColorDialog::SetPageOne.md)|將第一個屬性頁中的 RGB 值。|  
|[CMFCColorDialog::SetPageTwo](../Topic/CMFCColorDialog::SetPageTwo.md)|在第二個屬性頁中的 RGB 值。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|`m_bIsMyPalette`|`TRUE` ，如果色彩選取對話方塊中使用其色板或 `FALSE` ，如果  對話方塊中使用 `CMFCColorDialog` 在建構函式中指定的一個調色盤。|  
|`m_bPickerMode`|`TRUE` ，當使用者選取色彩從選取對話方塊時，否則， `FALSE`。|  
|`m_btnColorSelect`|使用者選取的色彩按鈕。|  
|`m_CurrentColor`|目前選取的色彩。|  
|`m_hcurPicker`|用來選取色彩的游標。|  
|`m_NewColor`|預期選取的色彩，可以永久地選取或還原為原始色彩。|  
|`m_pColourSheetOne`|為色彩選取屬性工作表的第一個屬性頁的指標。|  
|`m_pColourSheetTwo`|為色彩選取屬性工作表的第二個屬性頁的指標。|  
|`m_pPalette`|目前邏輯調色盤。|  
|`m_pPropSheet`|將屬性工作表的指標色彩選取對話方塊中的。|  
|`m_wndColors`|色彩選擇器控制項物件。|  
|`m_wndStaticPlaceHolder`|是色彩選擇器屬性工作表的預留位置的靜態控制項。|  
  
## 備註  
 色彩選取對話方塊中會顯示為有兩頁上的屬性工作表。  在第一個頁面，您可以選取標準色彩從系統調色盤，在第二頁，請選取自訂色彩。  
  
 您可以用在堆疊上 `CMFCColorDialog` 物件，然後呼叫 `DoModal`透過初始色彩當做參數傳遞至 `CMFCColorDialog` 建構函式。  色彩選取對話方塊會建立多個物件 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) 處理每個色板。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## 範例  
 您可以使用類別，在 `CMFCColorDialog` 的各種方法。下列範例將示範如何設定色彩對話方塊。  這個範例顯示如何設定目前和對話方塊的新色彩以及如何設定所選色彩的紅色，綠色和藍色色彩對話方塊的兩個屬性頁的。  這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#3](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#3)]  
  
## 需求  
 **標題:** afxcolordialog.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md)