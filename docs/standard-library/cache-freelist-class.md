---
title: "cache_freelist 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.cache_freelist"
  - "allocators/stdext::cache_freelist"
  - "stdext::cache_freelist"
  - "cache_freelist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_freelist 類別"
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# cache_freelist 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 [區塊配置器](../standard-library/allocators-header.md) 的配置及解除配置記憶體區塊的單一的大小。  
  
## 語法  
  
```  
template <std::size_t Sz, class Max> class cache_freelist  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Sz`|要配置的陣列中項目的數目。|  
|`Max`|最大的類別，表示可用清單的大小上限。 這可以是 [max\_fixed\_size](../standard-library/max-fixed-size-class.md), ，[max\_none](../standard-library/max-none-class.md), ，[max\_unbounded](../standard-library/max-unbounded-class.md), ，或 [max\_variable\_size](../standard-library/max-variable-size-class.md)。|  
  
## 備註  
 Cache\_freelist 樣板類別會維護可用的記憶體區塊大小的清單 `Sz`。 可用的清單已滿時它會使用 `operator delete` 解除配置記憶體區塊。 可用的清單是空的當它會使用 `operator new` 配置新的記憶體區塊。 可用清單的大小上限取決於的類別中的最大的類別傳遞 `Max` 參數。  
  
 每個記憶體區塊保留 `Sz` 可用的記憶體和資料的位元組， `operator new` 和 `operator delete` 需要。  
  
### 建構函式  
  
|||  
|-|-|  
|[cache\_freelist](../Topic/cache_freelist::cache_freelist.md)|建構類型 `cache_freelist` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[allocate](../Topic/cache_freelist::allocate.md)|配置記憶體區塊。|  
|[取消配置](../Topic/cache_freelist::deallocate.md)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)