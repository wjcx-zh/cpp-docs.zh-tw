---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f981b86ed8f5d3b240d9f02380a603eb4f2605bc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623585"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

定義數個範本，協助配置和釋放節點容器的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
#include <allocators>
```

> [!NOTE]
> \<allocators>已淘汰，從 Visual Studio 2019 16.3 版開始。

## <a name="remarks"></a>備註

\<allocators>標頭提供六個配置器範本，可用來選取以節點為基礎的容器的記憶體管理原則。 若與這些範本搭配使用，也可以提供數個不同的同步處理篩選，以將記憶體管理策略調整為數種不同的多執行緒配置 (包括無)。 您可以藉由將記憶體管理原則與記憶體使用量模式和同步處理需求進行比對，來加速應用程式或減少其記憶體需求。

使用可自訂或取代的可重複使用元件來實作配置器範本，以提供額外的記憶體管理策略。

C + + 標準程式庫中的以節點為基礎的容器（std：： list、std：： set、std：：多重集、std：： map 和 std：： multimap）會將其元素儲存在個別節點中。 特定容器類型的所有節點的大小都相同，因此不需要一般用途記憶體管理員的彈性。 因為在編譯時期就知道每個記憶體區塊的大小，所以記憶體管理員就會更簡單且快速。

與不是以節點為基礎的容器搭配使用時（例如，c + + 標準程式庫容器 std：： vector std：:d eque 和 std：： basic_string），配置器範本會正常運作，但不可能透過預設配置器提供任何效能改進。

配置器是一個類別樣板，其中描述的物件會管理物件的儲存空間配置和釋放，以及所指定類型之物件的陣列。 配置器物件是由 c + + 標準程式庫中的數個容器類別範本所使用。

配置器是此類型的所有範本︰

```cpp
template<class Type>
class allocator;
```

其中，範本引數 `Type` 是配置器執行個體所管理的類型。 C + + 標準程式庫提供預設配置器，類別樣板配置[器，其](allocator-class.md)定義于中 [\<memory>](memory.md) 。 \<allocators>標頭提供下列配置器：

- [allocator_newdel](allocator-newdel-class.md)

- [allocator_unbounded](allocator-unbounded-class.md)

- [allocator_fixed_size](allocator-fixed-size-class.md)

- [allocator_variable_size](allocator-variable-size-class.md)

- [allocator_suballoc](allocator-suballoc-class.md)

- [allocator_chunklist](allocator-chunklist-class.md)

建立容器時，使用配置器的適當具現化作為第二個類型引數，例如下列程式碼範例。

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 會配置具有 `allocator_chunklist` 的節點以及預設同步處理篩選。

使用 [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) 巨集，以使用預設值以外的同步處理篩選來建立配置器範本：

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 會配置具有 `allocator_chunklist` 的節點以及 [sync_per_thread](sync-per-thread-class.md)同步處理篩選。

區塊配置器是快取或篩選。 快取是一個類別樣板，其接受 std：： size_t 類型的一個引數。 它會定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。 它必須使用**new**運算子來取得記憶體，但不需要對每個區塊進行個別的 operator **new**呼叫。 例如，它會從較大的區塊進行子配置，或快取已解除配置的區塊以進行後續重新配置。

若編譯器無法重新系結樣板時所使用之 std：： size_t 引數的值，則不一定是傳遞至快取成員函式的引數值 _Sz 會配置和解除配置。

\<allocators>提供下列快取範本：

- [cache_freelist](cache-freelist-class.md)

- [cache_suballoc](cache-suballoc-class.md)

- [cache_chunklist](cache-chunklist-class.md)

篩選是使用另一個區塊配置器來執行其成員函式的區塊配置器，該配置函式會當做樣板引數傳遞給它。 最常見的篩選形式是同步處理篩選，其套用同步處理原則來控制對另一個區塊配置器執行個體之成員函式的存取。 \<allocators>提供下列同步處理篩選：

- [sync_none](sync-none-class.md)

- [sync_per_container](sync-per-container-class.md)

- [sync_per_thread](sync-per-thread-class.md)

- [sync_shared](sync-shared-class.md)

\<allocators>也會提供篩選[rts_alloc](rts-alloc-class.md)，其中包含多個區塊配置器實例，並決定在執行時間（而不是在編譯時期）用來配置或解除配置的實例。 它會搭配不可編譯重新繫結的編譯器使用。

同步處理原則決定配置器執行個體如何同時處理多個執行緒的配置和解除配置要求。 最簡單的原則是將所有要求直接傳遞給基礎快取物件，讓使用者同步處理管理。 更複雜的原則可以使用 Mutex 來序列化對基礎快取物件的存取。

如果編譯器支援編譯單一執行緒和多執行緒應用程式，則單一執行緒應用程式的同步處理篩選是 `sync_none`；在所有其他情況下，則是 `sync_shared`。

快取範本 `cache_freelist` 會採用 max 類別引數，以決定可在可用清單中儲存的元素數目上限。

\<allocators>提供下列最大類別：

- [max_none](max-none-class.md)

- [max_unbounded](max-unbounded-class.md)

- [max_fixed_size](max-fixed-size-class.md)

- [max_variable_size](max-variable-size-class.md)

### <a name="macros"></a>巨集

|巨集|描述|
|-|-|
|[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)|產生配置器類別範本。|
|[CACHE_CHUNKLIST](allocators-functions.md#cache_chunklist)|產生 `stdext::allocators::cache_chunklist<sizeof(Type)>`。|
|[CACHE_FREELIST](allocators-functions.md#cache_freelist)|產生 `stdext::allocators::cache_freelist<sizeof(Type), max>`。|
|[CACHE_SUBALLOC](allocators-functions.md#cache_suballoc)|產生 `stdext::allocators::cache_suballoc<sizeof(Type)>`。|
|[SYNC_DEFAULT](allocators-functions.md#sync_default)|產生同步處理篩選。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator！ = （ \<allocators> ）](allocators-operators.md#op_neq)|測試指定類別的配置器物件之間是否不等。|
|[operator = = （ \<allocators> ）](allocators-operators.md#op_eq_eq)|測試指定類別的配置器物件之間是否相等。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[allocator_base](allocator-base-class.md)|定義從同步處理篩選條件建立使用者定義的配置器時所需的基底類別和一般功能。|
|[allocator_chunklist](allocator-chunklist-class.md)|描述物件，該物件使用 [cache_chunklist](cache-chunklist-class.md) 類型的快取來管理物件的儲存空間配置和釋放。|
|[allocator_fixed_size](allocator-fixed-size-class.md)|描述物件，該物件搭配使用 [cache_freelist](cache-freelist-class.md) 類型的快取與 [max_fixed_size](max-fixed-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|
|[allocator_newdel](allocator-newdel-class.md)|執行配置器，它會使用**operator delete**來解除配置記憶體區塊，並使用**new 運算子**來配置記憶體區塊。|
|[allocator_suballoc](allocator-suballoc-class.md)|描述物件，該物件使用 [cache_suballoc](cache-suballoc-class.md) 類型的快取來管理 `Type`類型之物件的儲存空間配置和釋放。|
|[allocator_unbounded](allocator-unbounded-class.md)|描述物件，該物件搭配使用 [cache_freelist](cache-freelist-class.md) 類型的快取與 [max_unbounded](max-unbounded-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|
|[allocator_variable_size](allocator-variable-size-class.md)|描述物件，該物件搭配使用 [cache_freelist](cache-freelist-class.md) 類型的快取與 [max_variable_size](max-variable-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。|
|[cache_chunklist](cache-chunklist-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|
|[cache_freelist](cache-freelist-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|
|[cache_suballoc](cache-suballoc-class.md)|定義區塊配置器，以配置和解除配置單一大小的記憶體區塊。|
|[freelist](freelist-class.md)|可管理記憶體區塊的清單。|
|[max_fixed_size](max-fixed-size-class.md)|描述 max 類別物件，此物件可將 [freelist](freelist-class.md) 物件的長度上限限制為固定值。|
|[max_none](max-none-class.md)|描述 max 類別物件，此物件可將 [freelist](freelist-class.md) 物件的長度上限限制為零。|
|[max_unbounded](max-unbounded-class.md)|描述 max 類別物件，此物件不會限制 [freelist](freelist-class.md) 物件的長度上限。|
|[max_variable_size](max-variable-size-class.md)|描述 max 類別物件，此物件可將 [freelist](freelist-class.md) 物件的長度上限限制為與已配置的記憶體區塊數目大致成正比。|
|[rts_alloc](rts-alloc-class.md)|Rts_alloc 類別範本描述的[篩選準則](allocators-header.md)會保存快取實例的陣列，並判斷在執行時間（而不是編譯時期）配置和解除配置時所使用的實例。|
|[sync_none](sync-none-class.md)|描述未提供任何同步處理的同步處理篩選。|
|[sync_per_container](sync-per-container-class.md)|描述可為每個配置器物件提供不同快取物件的同步處理篩選。|
|[sync_per_thread](sync-per-thread-class.md)|描述可為每個執行緒提供不同快取物件的同步處理篩選。|
|[sync_shared](sync-shared-class.md)|描述同步處理篩選，使用 Mutex 來控制對所有配置器共用之快取物件的存取。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)
