---
title: "CMFCRibbonUndoButton Class | Microsoft Docs"
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
  - "CMFCRibbonUndoButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonUndoButton class"
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonUndoButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonUndoButton` 類別實作含有新使用者命令中的下拉式清單按鈕。  使用者可以選取一或多個最近命令從下拉式清單中加入取消復原或復原這些變更。  
  
## 語法  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](../Topic/CMFCRibbonUndoButton::CMFCRibbonUndoButton.md)|建構新的物件 `CMFCRibbonUndoButton` 使用命令 ID，您指定的文字標籤，然後從父代影像清單中的影像物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonUndoButton::AddUndoAction](../Topic/CMFCRibbonUndoButton::AddUndoAction.md)|加入新的動作加入動作清單。|  
|[CMFCRibbonUndoButton::CleanUpUndoList](../Topic/CMFCRibbonUndoButton::CleanUpUndoList.md)|清除動作清單，為下拉式清單。|  
|[CMFCRibbonUndoButton::GetActionNumber](../Topic/CMFCRibbonUndoButton::GetActionNumber.md)|判斷使用者從下拉式清單中選取項目的數目。|  
|[CMFCRibbonUndoButton::HasMenu](../Topic/CMFCRibbonUndoButton::HasMenu.md)|指出物件是否包含功能表。|  
  
## 備註  
 `CMFCRibbonUndoButton` 類別使用堆疊表示下拉式清單。  
  
## 範例  
 下列範例示範如何建構物件 `CMFCRibbonUndoButton` 類別，並加入新的動作加入動作清單。  這個程式碼片段是 [功能區小工具範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/CPP/cmfcribbonundobutton-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## 需求  
 **標題:** afxribbonundobutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)