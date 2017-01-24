---
title: "ABC 結構 | Microsoft Docs"
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
  - "ABC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ABC 結構"
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ABC 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**ABC** 結構在 TrueType 字型包含字元的寬度。  
  
## 語法  
  
```  
  
      typedef struct _ABC { /* abc */  
   int abcA;  
   UINT abcB;  
   int abcC;  
} ABC;  
```  
  
#### 參數  
 *abcA*  
 指定字元的 A 範圍。  A 範圍是在繪製字元圖像之前要加入至目前位置的距離。  
  
 *abcB*  
 指定字元的 B 範圍。  B 範圍是字元圖像繪製部分的寬度。  
  
 *abcC*  
 指定字元的 C 範圍。  C 範圍是要加入至目前位置的距離，以在字元圖像右邊加上空白字元。  
  
## 備註  
 字元的總寬度為 A、B 和 C 延伸的總和。  A 或 C 範圍可以是負數值，以標示留白部分或突出部分。  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)