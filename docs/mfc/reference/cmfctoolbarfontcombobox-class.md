---
title: "CMFCToolBarFontComboBox Class | Microsoft Docs"
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
  - "CMFCToolBarFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarFontComboBox class"
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
caps.latest.revision: 29
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含下拉式方塊控制項可讓使用者選取字型從系統字型清單的工具列按鈕。  
  
## 語法  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](../Topic/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox.md)|建構 `CMFCToolBarFontComboBox` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md)|傳回指向中指定索引處的物件。 `CMFCFontInfo` 下拉式方塊。|  
|[CMFCToolBarFontComboBox::SetFont](../Topic/CMFCToolBarFontComboBox::SetFont.md)|根據字型的字型名稱選取下拉式方塊中的字型、字型的前置詞和字元集。|  
  
### 資料成員  
 [CMFCToolBarFontComboBox::m\_nFontHeight](../Topic/CMFCToolBarFontComboBox::m_nFontHeight.md)  
 字元的高度 \(以字型下拉式方塊的。  
  
## 備註  
 若要將字型加入下拉式方塊按鈕加入至工具列，請依照下列步驟執行:  
  
1.  為按鈕保留虛擬資源 ID 在父代 \(Parent\) 工具列資源。  
  
2.  建構 `CMFCToolBarFontComboBox` 物件。  
  
3.  您可以使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，在處理 `AFX_WM_RESETTOOLBAR` 訊息的訊息處理常式，以新的下拉式方塊按鈕取代原始的按鈕。  
  
4.  同步處理使用 [CMFCToolBarFontComboBox::SetFont](../Topic/CMFCToolBarFontComboBox::SetFont.md) 方法，在具有字型的下拉式方塊中選取文件中的字型。  
  
 若要同步處理與下拉式方塊選取字型的字型的文件，請使用 [CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md) 方法擷取選取字型的屬性，並使用這些屬性來建立 [CFont Class](../../mfc/reference/cfont-class.md) 物件。  
  
 字型下拉式方塊按鈕呼叫 Win32 函式 [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) 判斷螢幕和印表機字型可用的系統。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
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