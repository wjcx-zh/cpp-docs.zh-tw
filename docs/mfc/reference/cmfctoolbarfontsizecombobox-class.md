---
title: "CMFCToolBarFontSizeComboBox Class | Microsoft Docs"
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
  - "CMFCToolBarFontSizeComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarFontSizeComboBox class"
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarFontSizeComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含下拉式方塊控制項可讓使用者選取字型大小的工具列按鈕。  
  
## 語法  
  
```  
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](../Topic/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox.md)|建構 `CMFCToolBarFontSizeComboBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarFontSizeComboBox::GetTwipSize](../Topic/CMFCToolBarFontSizeComboBox::GetTwipSize.md)|傳回以 Twip 為單位的選取的字型大小。|  
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](../Topic/CMFCToolBarFontSizeComboBox::RebuildFontSizes.md)|使用指定的字型的任何支援的字型大小填入下拉式清單。|  
|[CMFCToolBarFontSizeComboBox::SetTwipSize](../Topic/CMFCToolBarFontSizeComboBox::SetTwipSize.md)|設定以 Twip 為單位的字型大小。|  
  
## 備註  
 您可以使用 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 物件搭配使用 `CMFCToolBarFontSizeComboBox` 物件可讓使用者選取字型和字型大小。  
  
 如同您將字型下拉式方塊按鈕，您可以將字型大小下拉式方塊按鈕加入至工具列。  如需詳細資訊，請參閱 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)。  
  
 當使用者選取 `CMFCToolBarFontComboBox` 物件中建立新的字型，您可以使用 [CMFCToolBarFontSizeComboBox::RebuildFontSizes](../Topic/CMFCToolBarFontSizeComboBox::RebuildFontSizes.md) 方法，您可以使用這個字型的支援的大小來填滿字型大小下拉式方塊。  
  
## 範例  
 下列範例會在 `CMFCToolBarFontSizeComboBox` 類別會示範如何使用各種方法設定 `CMFCToolBarFontSizeComboBox` 物件。  以 Twip 範例將示範如何從文字方塊擷取字型大小，以 Twip 為單位，填滿，具有指定字型大小的任何有效的字型大小下拉式方塊，並指定字型大小。  這個程式碼片段是 [文字填補範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/CPP/cmfctoolbarfontsizecombobox-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)  
  
## 需求  
 **標題:** afxtoolbarfontcombobox.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)