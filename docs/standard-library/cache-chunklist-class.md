---
title: "cache_chunklist 類別 | Microsoft Docs"
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
  - "allocators/stdext::cache_chunklist"
  - "stdext.cache_chunklist"
  - "stdext::cache_chunklist"
  - "cache_chunklist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_chunklist 類別"
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: 17
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cache_chunklist 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義配置和解除配置單一大小的記憶體區塊的 [區塊配置器](../standard-library/allocators-header.md) 。  
  
## 語法  
  
```  
template <std::size_t Sz, std::size_t Nelts = 20> class cache_chunklist  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`Sz`|項目數目是陣列的配置。|  
  
## 備註  
 這個類別會使用 `operator new` 配置未經處理的記憶體區塊， suballocating 區塊配置記憶體區塊的儲存區，當需要;，當其記憶體區塊都不在使用中時，它會在每個區塊都不同的可用清單儲存解除配置的記憶體區塊，並使用 `operator delete` 取消配置區塊。  
  
 每個記憶體區塊保留 `Sz` 位元組可用的記憶體和指標區塊所屬。  每個區塊保留 `operator new` 和 `operator delete` 要求的 `Nelts` 記憶體區塊、三分球 int 和資料。  
  
### 建構函式  
  
|||  
|-|-|  
|[cache\_chunklist](../Topic/cache_chunklist::cache_chunklist.md)|建構屬於 `cache_chunklist` 類型的物件。|  
  
### 成員函式  
  
|||  
|-|-|  
|[配置](../Topic/cache_chunklist::allocate.md)|配置記憶體區塊。|  
|[解除配置](../Topic/cache_chunklist::deallocate.md)|從儲存體開始釋放物件所指定的數字在指定的位置。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<allocators\>](../standard-library/allocators-header.md)