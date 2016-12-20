---
title: "RECT 結構 | Microsoft Docs"
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
  - "LPRECT"
  - "RECT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LPRECT 結構"
  - "RECT 結構"
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RECT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`RECT` 結構定義矩形的左上角和右下角的座標。  
  
## 語法  
  
```  
  
      typedef struct tagRECT {   
   LONG left;  
   LONG top;  
   LONG right;  
   LONG bottom;  
} RECT;  
```  
  
## 成員  
 `left`  
 指定矩形左上角的 x 座標。  
  
 `top`  
 指定矩形左上角的 y 座標。  
  
 `right`  
 指定矩形右下角的 x 座標。  
  
 `bottom`  
 指定矩形右下角的 y 座標。  
  
## 範例  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/CPP/rect-structure1_1.cpp)]  
  
## 需求  
 **標頭 :** windef.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)