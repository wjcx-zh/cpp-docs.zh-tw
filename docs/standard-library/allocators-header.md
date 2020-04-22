---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f6be154be68cd5e43fd6f934d88c04fb25be9dc5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754425"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

定義數個範本，協助配置和釋放節點容器的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
#include <allocators>
```

> [!NOTE]
> \<從 Visual Studio 2019 版本 16.3 開始,分配器>被棄用。

## <a name="remarks"></a>備註

\<allocators> 標頭提供六種配置器範本可用來選取節點容器的記憶體管理策略。 若與這些範本搭配使用，也可以提供數個不同的同步處理篩選，以將記憶體管理策略調整為數種不同的多執行緒配置 (包括無)。 通過將記憶體管理原則與其記憶體使用模式和同步要求匹配,可以加快應用的速度,或降低其記憶體要求。

使用可自訂或取代的可重複使用元件來實作配置器範本，以提供額外的記憶體管理策略。

C++標準庫中基於節點的容器(std:list、std:set、std::多集、std::map 和 std::map)將其元素存儲在單個節點中。 特定容器類型的所有節點的大小都相同，因此不需要一般用途記憶體管理員的彈性。 因為在編譯時期就知道每個記憶體區塊的大小，所以記憶體管理員就會更簡單且快速。

當與不基於節點的容器(如C++標準庫容器(如C++標準庫容器std:vector std::deque和std::basic_string)一起使用時,分配器範本將正常工作,但不太可能提供與預設分配器相比的任何性能改進。

分配器是一個類範本,用於描述管理存儲分配和釋放指定類型對象的物件和陣列的物件。 分配器物件由標準庫中的多個容器類範本使用C++。

配置器是此類型的所有範本︰

```cpp
template<class Type>
class allocator;
```

其中，範本引數 `Type` 是配置器執行個體所管理的類型。 C++標準庫提供預設分配器,類範本[分配器](../standard-library/allocator-class.md),在[\<記憶體>](../standard-library/memory.md)定義。 \<allocators> 標頭提供下列配置器︰

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

建立容器時，使用配置器的適當具現化作為第二個類型引數，例如下列程式碼範例。

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 會配置具有 `allocator_chunklist` 的節點以及預設同步處理篩選。

使用 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 巨集，以使用預設值以外的同步處理篩選來建立配置器範本：

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 會配置具有 `allocator_chunklist` 的節點以及 [sync_per_thread](../standard-library/sync-per-thread-class.md)同步處理篩選。

區塊配置器是快取或篩選。 緩存是採用類型 std:::size_t 的參數的類範本。 它會定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。 它必須使用運算符**new**獲取記憶體,但它不需要為每個塊對運算元**進行單獨的新**調用。 例如，它會從較大的區塊進行子配置，或快取已解除配置的區塊以進行後續重新配置。

對於無法重新綁定實例化範本時使用的 std::size_t 參數的值的編譯器,不一定是傳遞給緩存的成員函數分配和解分配_Sz參數的值。

\<allocators> 提供下列快取範本︰

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

篩選器是一個塊分配器,它使用另一個塊分配器實現其成員函數,該分配器作為範本參數傳遞給它。 最常見的篩選形式是同步處理篩選，其套用同步處理原則來控制對另一個區塊配置器執行個體之成員函式的存取。 \<allocators> 提供下列同步處理篩選︰

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators> 也提供篩選 [rts_alloc](../standard-library/rts-alloc-class.md)，其可保留多個區塊配置器執行個體，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。 它會搭配不可編譯重新繫結的編譯器使用。

同步處理原則決定配置器執行個體如何同時處理多個執行緒的配置和解除配置要求。 最簡單的原則是將所有要求直接傳遞給基礎快取物件，讓使用者同步處理管理。 更複雜的原則可以使用 Mutex 來序列化對基礎快取物件的存取。

如果編譯器支援編譯單一執行緒和多執行緒應用程式，則單一執行緒應用程式的同步處理篩選是 `sync_none`；在所有其他情況下，則是 `sync_shared`。

快取樣本`cache_freelist`採用最大類參數,該參數確定要存儲在自由清單中的最大元素數。

\<allocators> 提供下列 max 類別︰

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>巨集

|巨集|描述|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|生成分配器類範本。|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|產生 `stdext::allocators::cache_chunklist<sizeof(Type)>`。|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|產生 `stdext::allocators::cache_freelist<sizeof(Type), max>`。|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|產生 `stdext::allocators::cache_suballoc<sizeof(Type)>`。|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|產生同步處理篩選。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子!*\<(分配器>)](../standard-library/allocators-operators.md#op_neq)|測試指定類別的配置器物件之間是否不等。|
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|測試指定類別的配置器物件之間是否相等。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|定義從同步處理篩選條件建立使用者定義的配置器時所需的基底類別和一般功能。|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|描述物件，該物件使用 [cache_chunklist](../standard-library/cache-chunklist-class.md) 類型的快取來管理物件的儲存空間配置和釋放。|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_fixed_size](../standard-library/max-fixed-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|實現使用**運算符刪除**來解分配記憶體區塊的分配器,實現**新運算符分配**記憶體區塊。|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|描述物件，該物件使用 [cache_suballoc](../standard-library/cache-suballoc-class.md) 類型的快取來管理 `Type`類型之物件的儲存空間配置和釋放。|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_unbounded](../standard-library/max-unbounded-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_variable_size](../standard-library/max-variable-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|
|[cache_freelist](../standard-library/cache-freelist-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|
|[freelist](../standard-library/freelist-class.md)|可管理記憶體區塊的清單。|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|描述 max 類別物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為固定值。|
|[max_none](../standard-library/max-none-class.md)|描述 max 類別物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為零。|
|[max_unbounded](../standard-library/max-unbounded-class.md)|描述 max 類別物件，此物件不會限制 [freelist](../standard-library/freelist-class.md) 物件的長度上限。|
|[max_variable_size](../standard-library/max-variable-size-class.md)|描述 max 類別物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為與已配置的記憶體區塊數目大致成正比。|
|[rts_alloc](../standard-library/rts-alloc-class.md)|rts_alloc類範本描述一個[篩選器](../standard-library/allocators-header.md),該篩選器包含緩存實例陣列,並確定在運行時而不是在編譯時使用哪個實例進行分配和分配。|
|[sync_none](../standard-library/sync-none-class.md)|描述未提供任何同步處理的同步處理篩選。|
|[sync_per_container](../standard-library/sync-per-container-class.md)|描述可為每個配置器物件提供不同快取物件的同步處理篩選。|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|描述可為每個執行緒提供不同快取物件的同步處理篩選。|
|[sync_shared](../standard-library/sync-shared-class.md)|描述同步處理篩選，使用 Mutex 來控制對所有配置器共用之快取物件的存取。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
