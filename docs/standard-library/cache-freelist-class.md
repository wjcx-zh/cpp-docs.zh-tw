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
ms.openlocfilehash: d757909d3e54fed35bf42b943b9f9740dffee115
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366741"
---
# <a name="cache_freelist-class"></a>cache_freelist 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*深圳*|所配置陣列中的元素數。|
|*麥克斯*|表示可用清單大小上限的 max 類別。 可以是 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>備註

cache_freelist類範本維護大小*Sz*的記憶體區塊的可用清單。 當可用清單已滿時,它使用**運算符刪除**來取消分配記憶體區塊。 當可用清單為空時,它使用**新運算元**來分配新的記憶體區塊。 可用清單的最大大小由*Max*參數中傳遞的類 max 類確定。

每個記憶體區都保存可用記憶體的*Sz*位元組以及**操作員新**和**運算元刪除**所需的資料。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_freelist](#cache_freelist)|建構類型 `cache_freelist` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[配置](#allocate)|配置記憶體區塊。|
|[去分配](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a>cache_freelist:分配

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a>cache_freelist:cache_freelist

建構類型 `cache_freelist` 的物件。

```cpp
cache_freelist();
```

### <a name="remarks"></a>備註

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a>cache_freelist::d分配

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

## <a name="see-also"></a>另請參閱

[\<配置器>](../standard-library/allocators-header.md)
