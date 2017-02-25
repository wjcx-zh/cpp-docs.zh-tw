---
title: "rts_alloc 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::rts_alloc"
  - "allocators/stdext::rts_alloc"
  - "rts_alloc"
  - "stdext.rts_alloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rts_alloc 類別"
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# rts_alloc 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

rts\_alloc 樣板類別描述一個[篩選條件](../standard-library/allocators-header.md)，該篩選條件可保留快取執行個體的陣列，並判斷在執行階段 \(而不是編譯時期\) 配置和解除配置時所使用的執行個體。  
  
## 語法  
  
```  
template <class Cache> class rts_alloc  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Cache`|包含在陣列中的快取執行個體類型，  可以是 [cache\_chunklist 類別](../standard-library/cache-chunklist-class.md)、[cache\_freelist](../standard-library/cache-freelist-class.md) 或 [cache\_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## 備註  
 這個樣板類別保留多個區塊配置器執行個體，並判斷在執行階段 \(而不是編譯時期\) 配置和解除配置時所使用的執行個體。  它會搭配不可編譯重新繫結的編譯器使用。  
  
### 成員函式  
  
|||  
|-|-|  
|[allocate](../Topic/rts_alloc::allocate.md)|配置記憶體區塊。|  
|[deallocate](../Topic/rts_alloc::deallocate.md)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
|[等於](../Topic/rts_alloc::equals.md)|比較兩個快取是否相等。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md)   
 [\<allocators\>](../standard-library/allocators-header.md)