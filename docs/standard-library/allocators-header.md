---
title: '&lt;allocators&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <allocators>
dev_langs:
- C++
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 386069d436c004dec19cd6edc7f5689971331227
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;
定義數個範本，協助配置和釋放節點容器的記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
#include <allocators>  
```  
  
## <a name="remarks"></a>備註  
 \<allocators> 標頭提供六種配置器範本可用來選取節點容器的記憶體管理策略。 若與這些範本搭配使用，也可以提供數個不同的同步處理篩選，以將記憶體管理策略調整為數種不同的多執行緒配置 (包括無)。 比對記憶體管理策略與特定應用程式的已知記憶體使用狀況模式和同步處理需求，通常可加快速度，或降低應用程式的整體記憶體需求。  
  
 使用可自訂或取代的可重複使用元件來實作配置器範本，以提供額外的記憶體管理策略。  
  
 C++ 標準程式庫中的節點容器 (std::list、std::set、std::multiset、std::map 和 std::multimap) 可將其元素儲存在個別節點中。 特定容器類型的所有節點的大小都相同，因此不需要一般用途記憶體管理員的彈性。 因為在編譯時期就知道每個記憶體區塊的大小，所以記憶體管理員就會更簡單且快速。  
  
 與非節點的容器 (例如 C++ 標準程式庫容器 std::vector、std::deque 和 std::basic_string) 搭配使用時，配置器範本將會正確運作，但可能無法透過預設配置器來提供任何效能改善。  
  
 配置器是一種範本類別，其所描述的物件管理物件和所指定類型物件陣列的儲存空間配置和釋放。 配置器物件是供 C++ 標準程式庫中的數個容器範本類別使用。  
  
 配置器是此類型的所有範本︰  
  
 `template<class` `Type` `>`  
  
 `class allocator;`  
  
 其中，範本引數 `Type` 是配置器執行個體所管理的類型。 C++ 標準程式庫會提供定義於 [\<memory>](../standard-library/memory.md)的預設配置器範本類別 [allocator](../standard-library/allocator-class.md)。 \<allocators> 標頭提供下列配置器︰  
  
- [allocator_newdel](../standard-library/allocator-newdel-class.md)  
  
- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)  
  
- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)  
  
- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)  
  
- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)  
  
- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 建立容器時，使用配置器的適當具現化作為第二個類型引數，例如下列程式碼範例。  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 _List0 會配置具有 `allocator_chunklist` 的節點以及預設同步處理篩選。  
  
 使用 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 巨集，以使用預設值以外的同步處理篩選來建立配置器範本：  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 _Lst1 會配置具有 `allocator_chunklist` 的節點以及 [sync_per_thread](../standard-library/sync-per-thread-class.md)同步處理篩選。  
  
 區塊配置器是快取或篩選。 快取是接受 std::size_t 類型之一個引數的範本類別。 它會定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。 它必須取得記憶體 using 運算子 `new`，但不需要個別呼叫每個區塊的運算子 `new`。 例如，它會從較大的區塊進行子配置，或快取已解除配置的區塊以進行後續重新配置。  
  
 如果編譯器無法編譯重新繫結在具現化範本時所使用的 std::size_t 引數值，則不一定是傳遞給快取成員函式配置和解除配置的 _Sz 引數值。  
  
 \<allocators> 提供下列快取範本︰  
  
- [cache_freelist](../standard-library/cache-freelist-class.md)  
  
- [cache_suballoc](../standard-library/cache-suballoc-class.md)  
  
- [cache_chunklist](../standard-library/cache-chunklist-class.md)  
  
 篩選是一個區塊配置器，可使用另一個作為範本引數傳遞給它的區塊配置器來實作其成員函式。 最常見的篩選形式是同步處理篩選，其套用同步處理原則來控制對另一個區塊配置器執行個體之成員函式的存取。 \<allocators> 提供下列同步處理篩選︰  
  
- [sync_none](../standard-library/sync-none-class.md)  
  
- [sync_per_container](../standard-library/sync-per-container-class.md)  
  
- [sync_per_thread](../standard-library/sync-per-thread-class.md)  
  
- [sync_shared](../standard-library/sync-shared-class.md)  
  
 \<allocators> 也提供篩選 [rts_alloc](../standard-library/rts-alloc-class.md)，其可保留多個區塊配置器執行個體，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。 它會搭配不可編譯重新繫結的編譯器使用。  
  
 同步處理原則決定配置器執行個體如何同時處理多個執行緒的配置和解除配置要求。 最簡單的原則是將所有要求直接傳遞給基礎快取物件，讓使用者同步處理管理。 更複雜的原則可以使用 Mutex 來序列化對基礎快取物件的存取。  
  
 如果編譯器支援編譯單一執行緒和多執行緒應用程式，則單一執行緒應用程式的同步處理篩選是 `sync_none`；在所有其他情況下，則是 `sync_shared`。  
  
 快取範本 `cache_freelist` 接受 max 類別引數，其決定可在可用清單中儲存的元素數目上限。  
  
 \<allocators> 提供下列 max 類別︰  
  
- [max_none](../standard-library/max-none-class.md)  
  
- [max_unbounded](../standard-library/max-unbounded-class.md)  
  
- [max_fixed_size](../standard-library/max-fixed-size-class.md)  
  
- [max_variable_size](../standard-library/max-variable-size-class.md)  
  
### <a name="macros"></a>巨集  
  
|||  
|-|-|  
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|產生配置器範本類別。|  
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|產生 `stdext::allocators::cache_chunklist<sizeof(Type)>`。|  
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|產生 `stdext::allocators::cache_freelist<sizeof(Type), max>`。|  
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|產生 `stdext::allocators::cache_suballoc<sizeof(Type)>`。|  
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|產生同步處理篩選。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator!= (\<allocators>)](../standard-library/allocators-operators.md#op_neq)|測試指定類別的配置器物件之間是否不等。|  
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|測試指定類別的配置器物件之間是否相等。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[allocator_base](../standard-library/allocator-base-class.md)|定義從同步處理篩選條件建立使用者定義的配置器時所需的基底類別和一般功能。|  
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|描述物件，該物件使用 [cache_chunklist](../standard-library/cache-chunklist-class.md) 類型的快取來管理物件的儲存空間配置和釋放。|  
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_fixed_size](../standard-library/max-fixed-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|  
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|實作配置器，以使用 `operator delete` 來解除配置記憶體區塊，以及使用 `operator new` 來配置記憶體區塊。|  
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|描述物件，該物件使用 [cache_suballoc](../standard-library/cache-suballoc-class.md) 類型的快取來管理 `Type`類型之物件的儲存空間配置和釋放。|  
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_unbounded](../standard-library/max-unbounded-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|  
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_variable_size](../standard-library/max-variable-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|  
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|  
|[cache_freelist](../standard-library/cache-freelist-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|  
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|  
|[freelist](../standard-library/freelist-class.md)|管理記憶體區塊的清單。|  
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|描述 max 類別物件，其可將 [freelist](../standard-library/freelist-class.md) 物件限制為固定最大長度。|  
|[max_none](../standard-library/max-none-class.md)|描述 max 類別物件，其可將 [freelist](../standard-library/freelist-class.md) 物件限制為零 (最大長度)。|  
|[max_unbounded](../standard-library/max-unbounded-class.md)|描述 max 類別物件，其不會限制 [freelist](../standard-library/freelist-class.md) 物件的最大長度。|  
|[max_variable_size](../standard-library/max-variable-size-class.md)|描述 max 類別物件，其可將 [freelist](../standard-library/freelist-class.md) 物件限制為與已配置記憶體區塊數目成正比的最大長度。|  
|[rts_alloc](../standard-library/rts-alloc-class.md)|rts_alloc 範本類別描述一個[篩選](../standard-library/allocators-header.md)，其可保留快取執行個體的陣列，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。|  
|[sync_none](../standard-library/sync-none-class.md)|描述未提供任何同步處理的同步處理篩選。|  
|[sync_per_container](../standard-library/sync-per-container-class.md)|描述可為每個配置器物件提供不同快取物件的同步處理篩選。|  
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|描述可為每個執行緒提供不同快取物件的同步處理篩選。|  
|[sync_shared](../standard-library/sync-shared-class.md)|描述同步處理篩選，使用 Mutex 來控制對所有配置器共用之快取物件的存取。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<allocators>  
  
 **命名空間：** stdext  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)



