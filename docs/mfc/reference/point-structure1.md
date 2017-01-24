---
title: "POINT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POINT"
  - "LPPOINT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPPOINT 結構"
  - "POINT 結構"
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# POINT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**POINT** 結構定義點的 X*\-* 和 Y 座標。  
  
## 語法  
  
```  
  
      typedef struct tagPOINT {  
   LONG x;  
   LONG y;  
} POINT;  
```  
  
#### 參數  
 *x*  
 指定點的 X 座標。  
  
 *y*  
 指定點的 Y 座標。  
  
## 範例  
 [!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/CPP/point-structure1_1.cpp)]  
  
## 需求  
 **標頭 :** windef.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPoint Class](../../atl-mfc-shared/reference/cpoint-class.md)