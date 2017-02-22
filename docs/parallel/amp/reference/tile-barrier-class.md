---
title: "tile_barrier 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tile_barrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tile_barrier 類別"
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# tile_barrier 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

利用 `wait` 方法同步處理在執行緒群組 \(磚\) 中執行的執行緒。  只有在執行階段才能執行個體化這個類別。  
  
## 語法  
  
```  
class tile_barrier;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[tile\_barrier::tile\_barrier 建構函式](../Topic/tile_barrier::tile_barrier%20Constructor.md)|初始化 `tile_barrier` 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md)|指示所有在執行緒群組 \(tile\) 中的執行緒停止執行，直至 tile 中的所有執行緒均已完成等待。|  
|[tile\_barrier::wait\_with\_all\_memory\_fence 方法](../Topic/tile_barrier::wait_with_all_memory_fence%20Method.md)|封鎖 Tile 中所有執行緒的執行，直到所有的記憶體存取已經完成，且 Tile 中的所有執行緒已經完成這個呼叫。|  
|[tile\_barrier::wait\_with\_global\_memory\_fence 方法](../Topic/tile_barrier::wait_with_global_memory_fence%20Method.md)|封鎖 Tile 中所有執行緒的執行，直到所有的全域記憶體存取已經完成，且 Tile 中的所有執行緒已經完成這個呼叫。|  
|[tile\_barrier::wait\_with\_tile\_static\_memory\_fence 方法](../Topic/tile_barrier::wait_with_tile_static_memory_fence%20Method.md)|封鎖 Tile 中所有執行緒的執行，直到所有的 `tile_static` 記憶體存取已經完成，且 Tile 中的所有執行緒已經完成這個呼叫。|  
  
## 繼承階層架構  
 `tile_barrier`  
  
## 需求  
 **標頭：**amp.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)