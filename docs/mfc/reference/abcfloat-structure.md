---
title: "ABCFLOAT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ABCFLOAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ABCFLOAT 結構"
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# ABCFLOAT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`ABCFLOAT` 結構包含字型字元 A、B 和 C 寬度。  
  
## 語法  
  
```  
  
      typedef struct _ABCFLOAT { /* abcf */  
   FLOAT abcfA;  
   FLOAT abcfB;  
   FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### 參數  
 *abcfA*  
 指定字元的 A 範圍。  A 範圍是在繪製字元圖像之前要加入至目前位置的距離。  
  
 *abcfB*  
 指定字元的 B 範圍。  B 範圍是字元圖像繪製部分的寬度。  
  
 *abcfC*  
 指定字元的 C 範圍。  C 範圍是要加入至目前位置的距離，以在字元圖像右邊加上空白字元。  
  
## 備註  
 A、B 和 C 寬度是沿著字型的基準線測量的。  一個字元的字元增量 \(總寬度\) 是 A、B 和 C 延伸的總和。  A 或 C 範圍可以是負數值，以標示留白部分或突出部分。  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)