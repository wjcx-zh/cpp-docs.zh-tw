---
title: "CMFCDragFrameImpl Class | Microsoft Docs"
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
  - "CMFCDragFrameImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDragFrameImpl class"
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDragFrameImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCDragFrameImpl` 類別繪製拖曳矩形外觀的使用者在標準固定模式拖曳一個窗格。  
  
## 語法  
  
```  
class CMFCDragFrameImpl  
```  
  
## 備註  
 這個類別會在每個物件 [CPane Class](../../mfc/reference/cpane-class.md) 內嵌物件。  因此，使用 `CanFloat` 方法的每一個窗格顯示拖曳矩形，則當使用者拖曳時。  
  
 您可以使用 [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessFloat](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat.md) 和 [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessDock](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock.md)，控制拖曳矩形的粗細。  
  
## 繼承階層架構  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## 需求  
 **標題:** afxdragframeimpl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessFloat](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat.md)   
 [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessDock](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock.md)