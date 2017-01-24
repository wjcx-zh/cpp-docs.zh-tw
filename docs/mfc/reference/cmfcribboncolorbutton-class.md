---
title: "CMFCRibbonColorButton 類別 | Microsoft Docs"
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
  - "CMFCRibbonColorButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonColorButton 類別"
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonColorButton 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonColorButton` 類別實作可以加入功能區列中的色彩按鈕。 功能區色彩按鈕會顯示包含一個或多個色板的下拉式功能表。  
  
## 語法  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](../Topic/CMFCRibbonColorButton::CMFCRibbonColorButton.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonColorButton::AddColorsGroup](../Topic/CMFCRibbonColorButton::AddColorsGroup.md)|將色彩群組加入標準色彩區域中。|  
|[CMFCRibbonColorButton::EnableAutomaticButton](../Topic/CMFCRibbonColorButton::EnableAutomaticButton.md)|指定是否啟用 \[自動\] 按鈕。|  
|[CMFCRibbonColorButton::EnableOtherButton](../Topic/CMFCRibbonColorButton::EnableOtherButton.md)|啟用 \[其他\] 按鈕。|  
|[CMFCRibbonColorButton::GetAutomaticColor](../Topic/CMFCRibbonColorButton::GetAutomaticColor.md)||  
|[CMFCRibbonColorButton::GetColor](../Topic/CMFCRibbonColorButton::GetColor.md)|傳回目前選取的色彩。|  
|[CMFCRibbonColorButton::GetColorBoxSize](../Topic/CMFCRibbonColorButton::GetColorBoxSize.md)|傳回色軸顯示的色彩項目大小。|  
|[CMFCRibbonColorButton::GetColumns](../Topic/CMFCRibbonColorButton::GetColumns.md)||  
|[CMFCRibbonColorButton::GetHighlightedColor](../Topic/CMFCRibbonColorButton::GetHighlightedColor.md)|傳回目前所選項目在快顯調色盤上的色彩。|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](../Topic/CMFCRibbonColorButton::RemoveAllColorGroups.md)|從標準色彩區域移除所有色彩群組。|  
|[CMFCRibbonColorButton::SetColor](../Topic/CMFCRibbonColorButton::SetColor.md)|從標準色彩區域選取色彩。|  
|[CMFCRibbonColorButton::SetColorBoxSize](../Topic/CMFCRibbonColorButton::SetColorBoxSize.md)|設定色軸顯示之所有色彩項目的大小。|  
|[CMFCRibbonColorButton::SetColorName](../Topic/CMFCRibbonColorButton::SetColorName.md)||  
|[CMFCRibbonColorButton::SetColumns](../Topic/CMFCRibbonColorButton::SetColumns.md)||  
|[CMFCRibbonColorButton::SetDocumentColors](../Topic/CMFCRibbonColorButton::SetDocumentColors.md)|指定文件色彩區域顯示的 RGB 值清單。|  
|[CMFCRibbonColorButton::SetPalette](../Topic/CMFCRibbonColorButton::SetPalette.md)||  
|[CMFCRibbonColorButton::UpdateColor](../Topic/CMFCRibbonColorButton::UpdateColor.md)||  
  
## 備註  
 當使用者按下它時，功能區色彩按鈕就會顯示色軸。 這個色軸預設包含色彩選取範圍的調色盤，稱為標準色彩區域。 色軸也可以選擇顯示 \[自動\] 按鈕，讓使用者選取預設的色彩，而 \[其他\] 按鈕則顯示包含其他色彩的快顯調色盤。  
  
## 範例  
 下例示範如何在 `CMFCRibbonColorButton` 類別中使用各種方法。 此範例示範如何建構 `CMFCRibbonColorButton` 物件、設定大型影像、啟用 \[自動\] 按鈕、啟用 \[其他\] 按鈕、設定資料行數目、設定色軸顯示的所有色彩項目大小、將色彩群組加入標準色彩區域中，以及指定文件色彩區域顯示的 RGB 值清單。 這段程式碼片段是 [Draw 用戶端範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/CPP/cmfcribboncolorbutton-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## 需求  
 **標題:** afxribboncolorbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)