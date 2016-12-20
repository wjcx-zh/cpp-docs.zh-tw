---
title: "&lt;allocators&gt; | Microsoft Docs"
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
  - "stdext::<allocators>"
  - "allocators/stdext::allocators"
  - "<allocators>"
  - "stdext.<allocators>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocators 標頭"
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;allocators&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義說明配置和釋放以節點的容器的記憶體區塊的範本。  
  
## 語法  
  
```  
#include <allocators>  
```  
  
## 備註  
 \<配置器\> 標題提供可用來為以節點的容器選取記憶體管理策略的六個配置器範本。  為與這些範本的使用，它也提供數個不同的同步處理篩選條件為記憶體管理策略以提供為各種多執行緒的計劃 \(包括無\)。  與記憶體管理原則為已知的記憶體使用模式和同步要求，特定應用程式通常增加速度或減少應用程式的整體記憶體需求。  
  
 配置器範本實作與可以自訂或取代提供額外的記憶體管理策略可重複使用的元件。  
  
 以節點的容器在 Standard C\+\+ 程式庫 \(std::list、std::set、std::multiset、std::map 和 std::multimap\) 中的個別節點儲存其項目。  特定容器型別的所有節點相同大小，因此，一個通用記憶體管理員的彈性不需要的。  由於每個記憶體區塊的大小在編譯階段，記憶體管理員會更簡單更快。  
  
 當使用沒有節點根據的容器 \(例如 Standard C\+\+ 程式庫容器 std::vector std::deque 和 std::basic\_string\)， alllocator 範本會正常運作，不過，無法提供在預設配置器的任何效能改善。  
  
 配置器是描述物件處理儲存區配置和釋放物件和陣列的指定型別的物件的樣板類別。  數個容器樣板類別使用配置器物件在 Standard C\+\+ 程式庫中。  
  
 配置器是這個型別的所有範本:  
  
 `template<class`  `Type` `>`  
  
 `class allocator;`  
  
 該樣板引數是 `Type` 型別所管理配置器執行個體。  Standard C\+\+ 程式庫提供預設配置器，樣板類別 [配置器](../standard-library/allocator-class.md)，在 [\<memory\>](../standard-library/memory.md)中定義。  \<配置器\> 標題提供下列配置器:  
  
-   [allocator\_newdel](../standard-library/allocator-newdel-class.md)  
  
-   [allocator\_unbounded](../standard-library/allocator-unbounded-class.md)  
  
-   [allocator\_fixed\_size](../standard-library/allocator-fixed-size-class.md)  
  
-   [allocator\_variable\_size](../standard-library/allocator-variable-size-class.md)  
  
-   [allocator\_suballoc](../standard-library/allocator-suballoc-class.md)  
  
-   [allocator\_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 表示建立容器，如下列程式碼範例時，請使用配置器的適當具現化為第二個型別引數。  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 \_List0 與 `allocator_chunklist` 的配置節點和預設同步篩選。  
  
 非預設值，使用 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) 巨集建立具有同步處理篩選條件的配置器範本:  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 \_Lst1 與 `allocator_chunklist` 和 [sync\_per\_thread](../standard-library/sync-per-thread-class.md) 同步處理篩選條件的設定節點。  
  
 區塊配置器是快取或篩選條件。  快取是採用型別 std::size\_t 的引數的樣板類別。  它定義了配置和解除配置單一大小的記憶體區塊的區塊配置器。  使用 `new`運算子，它必須取得記憶體，不過，它不需要進行個別呼叫對於運算子 `new` 每個區塊。  它可以，例如，從較大的區塊或快取解除配置區塊的 suballocate 後續轉散發的。  
  
 使用無法編譯重新繫結的編譯器 std::size\_t 引數中使用了樣板時產生不一定是引數 \_Sz 的值傳遞至快取的成員函式配置和解除配置。  
  
 \<配置器\> 提供下列快取範本:  
  
-   [cache\_freelist](../standard-library/cache-freelist-class.md)  
  
-   [cache\_suballoc](../standard-library/cache-suballoc-class.md)  
  
-   [cache\_chunklist](../standard-library/cache-chunklist-class.md)  
  
 篩選條件是實作其成員函式使用另一個區塊配置器傳入做為樣板引數的區塊配置器。  篩選條件最常見的形式是同步的篩選條件，將同步處理原則來控制對其他區塊配置器執行個體成員函式的存取。 \<配置器\> 提供同步處理下列篩選條件:  
  
-   [sync\_none](../standard-library/sync-none-class.md)  
  
-   [sync\_per\_container](../standard-library/sync-per-container-class.md)  
  
-   [sync\_per\_thread](../standard-library/sync-per-thread-class.md)  
  
-   [sync\_shared](../standard-library/sync-shared-class.md)  
  
 \<配置器\> 也提供篩選 [rts\_alloc](../standard-library/rts-alloc-class.md)，保留多個區塊配置器執行個體並決定要使用哪一個執行個體為設定或解除配置在執行階段而非編譯時期。  它使用無法編譯重新繫結的編譯器。  
  
 同步處理原則判斷配置器執行個體如何處理從多個執行緒同時配置和解除配置要求。  這項最簡單的原則是直接透過所有要求傳遞至基礎快取物件，離開同步對使用者。  一項更複雜的原則可使用 Mutex 序列化至基礎快取物件的存取。  
  
 如果編譯器支援編譯單一執行緒和多執行緒應用程式，單一執行緒應用程式的預設同步處理篩選條件是 `sync_none`;至於其他所有情況則為 `sync_shared`。  
  
 快取範本 `cache_freelist` 並判斷在可用清單中儲存項目的最大數目的最大類別引數。  
  
 \<配置器\> 提供下列最大類別:  
  
-   [max\_none](../standard-library/max-none-class.md)  
  
-   [max\_unbounded](../standard-library/max-unbounded-class.md)  
  
-   [max\_fixed\_size](../standard-library/max-fixed-size-class.md)  
  
-   [max\_variable\_size](../standard-library/max-variable-size-class.md)  
  
### 巨集  
  
|||  
|-|-|  
|[ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md)|產生配置器樣板類別。|  
|[CACHE\_CHUNKLIST](../Topic/CACHE_CHUNKLIST%20\(%3Callocators%3E\).md)|產生 `stdext::allocators::cache_chunklist<sizeof(Type)>`。|  
|[CACHE\_FREELIST](../Topic/CACHE_FREELIST%20\(%3Callocators%3E\).md)|產生 `stdext::allocators::cache_freelist<sizeof(Type), max>`。|  
|[CACHE\_SUBALLOC](../Topic/CACHE_SUBALLOC%20\(%3Callocators%3E\).md)|產生 `stdext::allocators::cache_suballoc<sizeof(Type)>`。|  
|[SYNC\_DEFAULT](../Topic/SYNC_DEFAULT%20\(%3Callocators%3E\).md)|產生同步篩選條件。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Callocators%3E\).md)|測試指定類別的配置器物件之間是否不相等。|  
|[operator\=\=](../Topic/operator==%20\(%3Callocators%3E\).md)|測試指定類別的配置器物件之間是否相等。|  
  
### 類別  
  
|||  
|-|-|  
|[allocator\_base](../standard-library/allocator-base-class.md)|定義必要的基底類別和共用函式會從同步處理篩選條件之使用者定義的配置器。|  
|[allocator\_chunklist](../standard-library/allocator-chunklist-class.md)|描述處理儲存區配置和釋放物件所使用的快取 [cache\_chunklist](../standard-library/cache-chunklist-class.md)型別的物件。|  
|[allocator\_fixed\_size](../standard-library/allocator-fixed-size-class.md)|描述處理儲存區配置和釋放 `Type` 型別的物件上使用快取型別 [cache\_freelist](../standard-library/cache-freelist-class.md) 與 [max\_fixed\_size](../standard-library/max-fixed-size-class.md)處理的長度的物件。|  
|[allocator\_newdel](../standard-library/allocator-newdel-class.md)|實作使用 `operator delete` 解除配置記憶體區塊和 `operator new` 配置的記憶體區塊的配置器。|  
|[allocator\_suballoc](../standard-library/allocator-suballoc-class.md)|描述處理儲存區配置和釋放 `Type` 型別的物件上使用快取 [cache\_suballoc](../standard-library/cache-suballoc-class.md)型別的物件。|  
|[allocator\_unbounded](../standard-library/allocator-unbounded-class.md)|描述處理儲存區配置和釋放 `Type` 型別的物件上使用快取型別 [cache\_freelist](../standard-library/cache-freelist-class.md) 與 [max\_unbounded](../standard-library/max-unbounded-class.md)處理的長度的物件。|  
|[allocator\_variable\_size](../standard-library/allocator-variable-size-class.md)|描述處理儲存區配置和釋放 `Type` 型別的物件上使用快取型別 [cache\_freelist](../standard-library/cache-freelist-class.md) 與 [max\_variable\_size](../standard-library/max-variable-size-class.md)處理的長度的物件。|  
|[cache\_chunklist](../standard-library/cache-chunklist-class.md)|定義配置和解除配置單一大小的記憶體區塊的區塊配置器。|  
|[cache\_freelist](../standard-library/cache-freelist-class.md)|定義配置和解除配置單一大小的記憶體區塊的區塊配置器。|  
|[cache\_suballoc](../standard-library/cache-suballoc-class.md)|定義配置和解除配置單一大小的記憶體區塊的區塊配置器。|  
|[freelist](../standard-library/freelist-class.md)|處理記憶體區塊清單。|  
|[max\_fixed\_size](../standard-library/max-fixed-size-class.md)|描述較大類別物件限制固定的最大長度的 [freelist](../standard-library/freelist-class.md) 物件。|  
|[max\_none](../standard-library/max-none-class.md)|描述較大類別物件限制的最大長度的 [freelist](../standard-library/freelist-class.md) 物件零。|  
|[max\_unbounded](../standard-library/max-unbounded-class.md)|描述不限制 [freelist](../standard-library/freelist-class.md) 物件的最大長度的最大類別物件。|  
|[max\_variable\_size](../standard-library/max-variable-size-class.md)|描述較大類別物件限制大約比例的對配置的記憶體區塊數的最大長度的 [freelist](../standard-library/freelist-class.md) 物件。|  
|[rts\_alloc](../standard-library/rts-alloc-class.md)|保存快取執行個體的 rts\_alloc 樣板類別描述 [篩選條件](../standard-library/allocators-header.md) 並決定要使用哪一個執行個體為配置和解除配置在執行階段而非編譯時期。|  
|[sync\_none](../standard-library/sync-none-class.md)|描述並不提供同步的同步處理篩選條件。|  
|[sync\_per\_container](../standard-library/sync-per-container-class.md)|描述針對每個配置器物件提供不同的快取物件的同步處理篩選條件。|  
|[sync\_per\_thread](../standard-library/sync-per-thread-class.md)|描述針對每一個執行緒提供不同的快取物件的同步處理篩選條件。|  
|[sync\_shared](../standard-library/sync-shared-class.md)|描述使用 Mutex 控制對快取物件的存取由所有配置器共用的同步處理篩選條件。|  
  
## 需求  
 **標題:** \<配置器\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)