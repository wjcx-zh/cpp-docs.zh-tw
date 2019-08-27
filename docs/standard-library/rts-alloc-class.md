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
ms.openlocfilehash: 065c0eaf936a438f48dbb8aa28704e0f53926a03
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451130"
---
# <a name="rtsalloc-class"></a>rts_alloc 類別

rts_alloc 樣板類別描述一個[篩選](../standard-library/allocators-header.md)，其可保留快取執行個體的陣列，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。

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

這個樣板類別保留多個區塊配置器執行個體，並判斷在執行階段 (而不是編譯時期) 配置和解除配置時所使用的執行個體。 它會搭配不可編譯重新繫結的編譯器使用。

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="allocate"></a>  rts_alloc::allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*計數*|所配置陣列中的元素數。|

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

此`caches[_IDX].allocate(count)`成員函式會傳回, 其中`_IDX`索引取決於所要求的區塊大小*計數*, 或者, 如果*count*太大, 則會`operator new(count)`傳回。 `cache`，代表快取物件。

## <a name="deallocate"></a>  rts_alloc::deallocate

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|要從儲存體解除配置之第一個物件的指標。|
|*計數*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

此成員函式`caches[_IDX].deallocate(ptr, count)`會呼叫, 其中`_IDX`索引取決於所要求的區塊大小*計數*, 或者, 如果*計數*太大, 則會`operator delete(ptr)`傳回。

## <a name="equals"></a>  rts_alloc::equals

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

如果的結果`caches[0].equals(other.caches[0])`, 則為 true, 否則為**false**。 `caches` 代表快取物件的陣列。

## <a name="see-also"></a>另請參閱

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
