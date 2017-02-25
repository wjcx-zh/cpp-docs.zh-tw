---
title: "MINMAXINFO 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MINMAXINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MINMAXINFO 結構"
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# MINMAXINFO 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`MINMAXINFO` 結構包含視窗最大化大小的資訊和位置和它的最小值和最大值追蹤大小。  
  
## 語法  
  
```  
  
      typedef struct tagMINMAXINFO {  
   POINT ptReserved;  
   POINT ptMaxSize;  
   POINT ptMaxPosition;  
   POINT ptMinTrackSize;  
   POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### 參數  
 *ptReserved*  
 保留供內部使用。  
  
 *ptMaxSize*  
 指定這個最大化的寬度 \(point.x\) 和最大化的高度 \(point.y\) 視窗。  
  
 `ptMaxPosition`  
 指定最大化的視窗 \(point.x\) 左邊的位置和最大化的視窗 \(point.y\) 的頂端位置。  
  
 *ptMinTrackSize*  
 指定最小追蹤寬度 \(point.x\) 和最小追蹤高度 \(point.y\) 視窗。  
  
 *ptMaxTrackSize*  
 指定最大追蹤寬度 \(point.x\) 和最大追蹤高度 \(point.y\) 視窗。  
  
## 需求  
 **Header:** 中  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../Topic/CWnd::OnGetMinMaxInfo.md)