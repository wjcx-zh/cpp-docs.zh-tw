---
title: "CMFCColorMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCColorMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorMenuButton class"
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CMFCColorMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorMenuButton` 類別支援命令或啟動色彩選擇器對話方塊中的工具列按鈕。  
  
## 語法  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](../Topic/CMFCColorMenuButton::CMFCColorMenuButton.md)|建構 `CMFCColorMenuButton` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorMenuButton::EnableAutomaticButton](../Topic/CMFCColorMenuButton::EnableAutomaticButton.md)|啟用和停用規則色彩按鈕上的「Auto」按鈕。  \(標準系統自動按鈕標記 \[**自動**\]\)。|  
|[CMFCColorMenuButton::EnableDocumentColors](../Topic/CMFCColorMenuButton::EnableDocumentColors.md)|啟用資料特定色彩顯示 \(而不是系統色彩。|  
|[CMFCColorMenuButton::EnableOtherButton](../Topic/CMFCColorMenuButton::EnableOtherButton.md)|啟用和停用規則色彩\] 按鈕下方定位「其他」按鈕。  \(標準系統「其他」按鈕標記 \[**更多色彩…**\]\)。|  
|[CMFCColorMenuButton::EnableTearOff](../Topic/CMFCColorMenuButton::EnableTearOff.md)|以啟用未色彩窗格。|  
|[CMFCColorMenuButton::GetAutomaticColor](../Topic/CMFCColorMenuButton::GetAutomaticColor.md)|擷取目前的自動色彩。|  
|[CMFCColorMenuButton::GetColor](../Topic/CMFCColorMenuButton::GetColor.md)|擷取目前按鈕的色彩。|  
|[CMFCColorMenuButton::GetColorByCmdID](../Topic/CMFCColorMenuButton::GetColorByCmdID.md)|擷取對應於指定的命令 ID. 的色彩。|  
|[CMFCColorMenuButton::OnChangeParentWnd](../Topic/CMFCColorMenuButton::OnChangeParentWnd.md)|呼叫框架，當父視窗變更。|  
|[CMFCColorMenuButton::OpenColorDialog](../Topic/CMFCColorMenuButton::OpenColorDialog.md)|開啟色彩選取對話方塊。|  
|[CMFCColorMenuButton::SetColor](../Topic/CMFCColorMenuButton::SetColor.md)|設定目前色彩按鈕的色彩。|  
|[CMFCColorMenuButton::SetColorByCmdID](../Topic/CMFCColorMenuButton::SetColorByCmdID.md)|設定所指定的色彩功能表按鈕的色彩。|  
|[CMFCColorMenuButton::SetColorName](../Topic/CMFCColorMenuButton::SetColorName.md)|設定新名稱指定的色彩。|  
|[CMFCColorMenuButton::SetColumnsNumber](../Topic/CMFCColorMenuButton::SetColumnsNumber.md)|設定由 `CMFCColorBar` 物件顯示的欄數。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCColorMenuButton::CopyFrom](../Topic/CMFCColorMenuButton::CopyFrom.md)|複製到另一個工具列按鈕加入至目前的按鈕。|  
|[CMFCColorMenuButton::CreatePopupMenu](../Topic/CMFCColorMenuButton::CreatePopupMenu.md)|建立色彩選擇器對話方塊。|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](../Topic/CMFCColorMenuButton::IsEmptyMenuAllowed.md)|表示空的功能表是否支援。|  
|[CMFCColorMenuButton::OnDraw](../Topic/CMFCColorMenuButton::OnDraw.md)|呼叫由架構在按鈕上顯示影像。|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](../Topic/CMFCColorMenuButton::OnDrawOnCustomizeList.md)|呼叫框架，在 `CMFCColorMenuButton` 物件在工具列自訂對話方塊的  清單中目前已顯示。|  
  
## 備註  
 以 `CMFCColorMenuButton` 物件要取代原始的功能表或工具列按鈕，請建立物件， `CMFCColorMenuButton` 設定任何適當的 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) 樣式，然後呼叫 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) 類別的 `ReplaceButton` 方法。  如果您使用自訂的工具列，請呼叫方法。 [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md)  
  
 在處理 [CMFCColorMenuButton::CreatePopupMenu](../Topic/CMFCColorMenuButton::CreatePopupMenu.md) 事件處理常式期間，色彩選擇器對話方塊建立。  事件處理常式會 `WM_COMMAND` 告知訊息的父框架。  `CMFCColorMenuButton` 物件傳送指派至原始的功能表或工具列按鈕的控制項 ID。  
  
## 範例  
 您可以使用類別，在 `CMFCColorMenuButton` 的各種方法。下列範例將示範如何建立和設定色彩功能表按鈕。  在此範例中， `CPalette` 物件會先建立並用來建構物件 `CMFCColorMenuButton` 類別。  啟用的自動和其他按鈕並設定它的色彩和資料行編號然後設定 `CMFCColorMenuButton` 物件。  這個程式碼是 [文字填補範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/CPP/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/CPP/cmfccolormenubutton-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## 需求  
 **標題:** afxcolormenubutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)