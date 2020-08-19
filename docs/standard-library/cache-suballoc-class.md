---
title: cache_suballoc 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 410cdc7bd45c54c252ce33c7d8e3e2f883ac0eb4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560617"
---
# <a name="cache_suballoc-class"></a>cache_suballoc 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>參數

*深圳*\
所配置陣列中的元素數。

## <a name="remarks"></a>備註

Cache_suballoc 類別範本會將解除配置的記憶體區塊儲存在無限制長度的可用清單中， `freelist<sizeof(Type), max_unbounded>` 並在可用清單為空白時，從使用 **operator new** 所配置的較大區塊中 suballocates 記憶體區塊。

每個區塊都保留 `Sz * Nelts` 可用記憶體的位元組，以及 **運算子 new** 和 **operator delete** 所需的資料。 永遠不會釋放已配置的區塊。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_suballoc](#cache_suballoc)|建構類型 `cache_suballoc` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a> cache_suballoc：： allocate

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a> cache_suballoc：： cache_suballoc

建構類型 `cache_suballoc` 的物件。

```cpp
cache_suballoc();
```

### <a name="remarks"></a>備註

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a> cache_suballoc：:d eallocate

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
