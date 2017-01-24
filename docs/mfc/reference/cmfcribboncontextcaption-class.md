---
title: "CMFCRibbonContextCaption Class | Microsoft Docs"
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
  - "CMFCRibbonContextCaption"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonContextCaption class"
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonContextCaption Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作出現在功能區類別或內容類別頂端的彩色標題。  
  
## 語法  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonContextCaption::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonContextCaption::GetColor](../Topic/CMFCRibbonContextCaption::GetColor.md)|傳回標題的色彩。|  
|[CMFCRibbonContextCaption::GetRightTabX](../Topic/CMFCRibbonContextCaption::GetRightTabX.md)||  
|`CMFCRibbonContextCaption::GetThisClass`|由取得與此類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件標的架構使用。|  
  
## 備註  
 此類別無法直接具現化。  [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) 類別會在內部使用此類別，將色彩加入至功能區分類。  
  
 若要設定功能區分類的色彩，請呼叫 [CMFCRibbonCategory::SetTabColor](../Topic/CMFCRibbonCategory::SetTabColor.md)。  若要設定內容分類的色彩，請呼叫 [CMFCRibbonBar::AddContextCategory](../Topic/CMFCRibbonBar::AddContextCategory.md)。  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## 需求  
 **標頭：** afxRibbonBar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)