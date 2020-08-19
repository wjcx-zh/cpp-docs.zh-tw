---
title: sync_none 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: dac4dc1182de32af485d37a00ff96370ea8d8943
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562112"
---
# <a name="sync_none-class"></a>sync_none 類別

描述未提供任何同步處理的[同步處理篩選](../standard-library/allocators-header.md)。

## <a name="syntax"></a>語法

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>參數

`Cache`\
與同步處理篩選相關聯的快取類型。 它可以是 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) 、 [`cache_freelist`](../standard-library/cache-freelist-class.md) 或 [`cache_suballoc`](../standard-library/cache-suballoc-class.md) 。

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[分配](#allocate)|配置記憶體區塊。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a> sync_none：： allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

*計數*\
所配置陣列中的元素數。

### <a name="remarks"></a>備註

成員函式會傳回 `cache.allocate(count)`，其中 `cache` 是快取物件。

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a> sync_none：:d eallocate

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

成員函式會呼叫 `cache.deallocate(ptr, count)`，其中 `cache` 代表快取物件。

## <a name="sync_noneequals"></a><a name="equals"></a> sync_none：： equals

比較兩個快取是否相等。

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>參數

*緩存*\
同步處理篩選的快取物件。

*其他*\
要比較是否相等的快取物件。

### <a name="return-value"></a>傳回值

成員函式一律會傳回 **`true`** 。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
