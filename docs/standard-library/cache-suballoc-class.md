---
title: "cache_suballoc 類別 | Microsoft Docs"
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
  - "stdext.cache_suballoc"
  - "allocators/stdext::cache_suballoc"
  - "stdext::cache_suballoc"
  - "cache_suballoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_suballoc 類別"
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 17
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cache_suballoc 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 [區塊配置器](../standard-library/allocators-header.md) 的配置及解除配置記憶體區塊的單一的大小。  
  
## 語法  
  
```  
template <std::size_t Sz, size_t Nelts = 20> class cache_suballoc  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|`Sz`|要配置的陣列中項目的數目。|  
  
## 備註  
 Cache\_suballoc 樣板類別中可用的清單，以及未繫結的長度，儲存已配置的記憶體區塊使用 `freelist<sizeof(Type), max_unbounded>`, ，suballocates 從較大的區塊，以配置記憶體區塊和 `operator new` 時可用的清單是空的。  
  
 每個區塊保留 `Sz * Nelts` 可用的記憶體和資料的位元組， `operator new` 和 `operator delete` 需要。 永遠不會釋放已配置的區塊。  
  
### 建構函式  
  
|||  
|-|-|  
|[cache\_suballoc](../Topic/cache_suballoc::cache_suballoc.md)|建構類型 `cache_suballoc` 的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[allocate](../Topic/cache_suballoc::allocate.md)|配置記憶體區塊。|  
|[取消配置](../Topic/cache_suballoc::deallocate.md)|從指定位置起算的儲存體中，釋放指定數目的物件。|  
  
## 需求  
 **標頭：**\<allocators\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)