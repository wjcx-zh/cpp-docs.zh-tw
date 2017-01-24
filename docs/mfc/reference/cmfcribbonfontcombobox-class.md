---
title: "CMFCRibbonFontComboBox Class | Microsoft Docs"
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
  - "CMFCRibbonFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonFontComboBox class"
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作包含字型清單的下拉式方塊。  您可以在功能區面板上放置下拉式方塊。  
  
## 語法  
  
```  
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|解構函式。|  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](../Topic/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox.md)|建構並初始化 `CMFCRibbonFontComboBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonFontComboBox::BuildFonts](../Topic/CMFCRibbonFontComboBox::BuildFonts.md)|在功能區字型下拉式方塊中填入指定字型類型的字型、字元集，及字距和系列。|  
|`CMFCRibbonFontComboBox::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonFontComboBox::GetCharSet](../Topic/CMFCRibbonFontComboBox::GetCharSet.md)|傳回指定的字元集。|  
|[CMFCRibbonFontComboBox::GetFontDesc](../Topic/CMFCRibbonFontComboBox::GetFontDesc.md)||  
|[CMFCRibbonFontComboBox::GetFontType](../Topic/CMFCRibbonFontComboBox::GetFontType.md)|傳回要在下拉式方塊中顯示的字型類型。  有效的選項為 DEVICE\_FONTTYPE、RASTER\_FONTTYPE 和 TRUETYPE\_FONTTYPE，或任何位元組合。|  
|[CMFCRibbonFontComboBox::GetPitchAndFamily](../Topic/CMFCRibbonFontComboBox::GetPitchAndFamily.md)|傳回在下拉式方塊中顯示之字型的字距和系列。|  
|`CMFCRibbonFontComboBox::GetThisClass`|由取得與此類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件標的架構使用。|  
|[CMFCRibbonFontComboBox::RebuildFonts](../Topic/CMFCRibbonFontComboBox::RebuildFonts.md)|在功能區字型下拉式方塊中填入先前指定之字型類型的字型、字元集，及字距和系列。|  
|[CMFCRibbonFontComboBox::SetFont](../Topic/CMFCRibbonFontComboBox::SetFont.md)|在下拉式方塊中選取指定的字型。|  
  
## 備註  
 建立 `CMFCRibbonFontComboBox` 物件後，藉由呼叫 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md) 將它加入至功能區面板中。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
 [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)  
  
## 需求  
 **標頭：** afxRibbonComboBox.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonComboBox Class](../../mfc/reference/cmfcribboncombobox-class.md)