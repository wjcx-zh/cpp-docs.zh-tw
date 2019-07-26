---
title: cache_freelist 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: 05260d6800597b64908ff0aeffac47b09fed9a0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449692"
---
# <a name="cachefreelist-class"></a>cache_freelist 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Sz*|所配置陣列中的元素數。|
|*最大值*|表示可用清單大小上限的 max 類別。 可以是 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>備註

Cache_freelist 範本類別會維護一份大小為*Sz*的記憶體區塊的免費清單。 當免費清單已滿時, 會使用**運算子 delete**來解除配置記憶體區塊。 當免費清單是空的時, 它會使用**operator new**來配置新的記憶體區塊。 可用清單的大小上限取決於*最大值*參數中傳遞的類別 max 類別。

每個記憶體區塊會保留可使用記憶體的*Sz*位元組, 以及**operator new**和**operator delete**所需的資料。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[cache_freelist](#cache_freelist)|建構類型 `cache_freelist` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|說明|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="allocate"></a>  cache_freelist::allocate

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

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

建構類型 `cache_freelist` 的物件。

```cpp
cache_freelist();
```

### <a name="remarks"></a>備註

## <a name="deallocate"></a>  cache_freelist::deallocate

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

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
