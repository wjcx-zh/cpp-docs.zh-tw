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
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373417"
---
# <a name="rts_alloc-class"></a>rts_alloc 類別

rts_alloc類範本描述一個[篩選器](../standard-library/allocators-header.md),該篩選器包含緩存實例陣列,並確定在運行時而不是在編譯時使用哪個實例進行分配和分配。

## <a name="syntax"></a>語法

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*快取*|包含在陣列中的快取執行個體類型， 這可以是 [cache_chunklist Class](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

## <a name="remarks"></a>備註

此類範本包含多個塊分配器實例,並確定在運行時而不是在編譯時使用哪個實例進行分配或分配。 它會搭配不可編譯重新繫結的編譯器使用。

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[配置](#allocate)|配置記憶體區塊。|
|[去分配](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc::分配

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*count*|所配置陣列中的元素數。|

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

成員函數`caches[_IDX].allocate(count)`傳回 ,`_IDX`其中索引 由請求的區塊*大小 計數*確定,或者,`operator new(count)`如果*計數*太大,則傳回 。 `cache`，代表快取物件。

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::d分配

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Ptr*|要從儲存空間解除配置之第一個物件的指標。|
|*count*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

成員函數`caches[_IDX].deallocate(ptr, count)`呼叫 ,其中`_IDX`索引 由請求的塊大小*計數*確定,或者,如果*計數*太大,則傳回`operator delete(ptr)`。

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc:等於

比較兩個快取是否相等。

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Cache*|與篩選條件相關聯的快取物件。|
|*_Other*|要比較是否相等的快取物件。|

### <a name="remarks"></a>備註

**如果 為**`caches[0].equals(other.caches[0])`,則 為否則,**假**。 `caches` 代表快取物件的陣列。

## <a name="see-also"></a>另請參閱

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<配置器>](../standard-library/allocators-header.md)
