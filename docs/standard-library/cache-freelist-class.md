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
ms.openlocfilehash: bbe0ff0f2297afcec99bd162ebe6a6d3e10f9bce
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560722"
---
# <a name="cache_freelist-class"></a>cache_freelist 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>參數

*深圳*\
所配置陣列中的元素數。

*麥克斯*\
表示可用清單大小上限的 max 類別。 可以是 [max_fixed_size](../standard-library/max-fixed-size-class.md)、[max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。

## <a name="remarks"></a>備註

Cache_freelist 類別範本會維護一個大小為 *Sz*之記憶體區塊的可用清單。 當免費清單填滿時，會使用 **operator delete** 來解除配置記憶體區塊。 當可用清單空白時，就會使用 **operator new** 來配置新的記憶體區塊。 可用清單的大小上限是由 *最大值* 參數中傳遞的類別 max 類別所決定。

每個記憶體區塊都會保存可使用記憶體的 *Sz* 位元組，以及 **運算子 new** 和 **operator delete** 所需的資料。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_freelist](#cache_freelist)|建構類型 `cache_freelist` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a> cache_freelist：： allocate

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a> cache_freelist：： cache_freelist

建構類型 `cache_freelist` 的物件。

```cpp
cache_freelist();
```

### <a name="remarks"></a>備註

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a> cache_freelist：:d eallocate

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

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
