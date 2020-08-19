---
title: rts_alloc 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: 04a6578c7abd07ff84f4c0a5cee68cfd7ec8ef04
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560552"
---
# <a name="rts_alloc-class"></a>rts_alloc 類別

Rts_alloc 類別樣板描述的 [篩選](../standard-library/allocators-header.md) 會保存快取實例的陣列，並判斷在執行時間（而不是編譯時期）配置和解除配置時所使用的實例。

## <a name="syntax"></a>語法

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>參數

*緩存*\
包含在陣列中的快取執行個體類型， 它可以是 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) 、 [`cache_freelist`](../standard-library/cache-freelist-class.md) 或 [`cache_suballoc`](../standard-library/cache-suballoc-class.md) 。

## <a name="remarks"></a>備註

這個類別樣板會保存多個區塊配置器實例，並判斷在執行時間（而不是編譯時期）配置或解除配置時要使用的實例。 它會搭配不可編譯重新繫結的編譯器使用。

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[分配](#allocate)|配置記憶體區塊。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a> rts_alloc：： allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

*計數*\
所配置陣列中的元素數。

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

成員函式 `caches[_IDX].allocate(count)` 會傳回，其中索引 `_IDX` 取決於要求的區塊大小 *計數*，或者，如果 *計數* 太大，則會傳回 `operator new(count)` 。 `cache`，代表快取物件。

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a> rts_alloc：:d eallocate

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>參數

*Ptr*\
要從儲存空間解除配置之第一個物件的指標。

*計數*\
要從儲存空間解除配置的物件數目。

### <a name="remarks"></a>備註

成員函式 `caches[_IDX].deallocate(ptr, count)` 會呼叫，其中索引 `_IDX` 取決於要求的區塊大小 *計數*，或者，如果 *計數* 太大，則會傳回 `operator delete(ptr)` 。

## <a name="rts_allocequals"></a><a name="equals"></a> rts_alloc：： equals

比較兩個快取是否相等。

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>參數

*_Cache*\
與篩選條件相關聯的快取物件。

*_Other*\
要比較是否相等的快取物件。

### <a name="remarks"></a>備註

**`true`** 如果的結果 `caches[0].equals(other.caches[0])` ，則為，否則為 **`false`** 。 `caches` 代表快取物件的陣列。

## <a name="see-also"></a>另請參閱

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
