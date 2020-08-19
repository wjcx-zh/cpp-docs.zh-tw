---
title: sync_per_thread 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
ms.openlocfilehash: 24c5463dc9fb80703361e374efb99fae9e103e7c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562086"
---
# <a name="sync_per_thread-class"></a>sync_per_thread 類別

描述可為每個執行緒物件提供不同快取物件的[同步處理篩選](../standard-library/allocators-header.md)。

## <a name="syntax"></a>語法

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>參數

*緩存*\
與同步處理篩選相關聯的快取類型。 它可以是 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) 、 [`cache_freelist`](../standard-library/cache-freelist-class.md) 或 [`cache_suballoc`](../standard-library/cache-suballoc-class.md) 。

## <a name="remarks"></a>備註

即使無法從另一個執行緒中取消配置某個執行緒中配置的區塊，使用 `sync_per_thread` 的配置器還是可以比較是否相等。 當您使用這其中一個配置器時，其他執行緒應該看不到某個執行緒中配置的記憶體區塊。 實際上，這表示使用這其中一個配置器的容器只能透過單一執行緒來存取。

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="sync_per_threadallocate"></a><a name="allocate"></a> sync_per_thread：： allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

*計數*\
所配置陣列中的元素數。

### <a name="remarks"></a>備註

成員函式會在屬於目前執行緒的快取物件上傳回 `cache::allocate(count)` 呼叫的結果。 如果未針對目前的執行緒配置任何快取物件，則它會先配置一個。

## <a name="sync_per_threaddeallocate"></a><a name="deallocate"></a> sync_per_thread：:d eallocate

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

成員函式會在屬於目前執行緒的快取物件上呼叫 `deallocate`。 如果未針對目前的執行緒配置任何快取物件，則它會先配置一個。

## <a name="sync_per_threadequals"></a><a name="equals"></a> sync_per_thread：： equals

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

**`false`** 如果未配置任何快取物件給這個物件或目前線程中的 *其他* 物件。 否則會傳回將 `operator==` 套用到這兩個快取物件的結果。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
