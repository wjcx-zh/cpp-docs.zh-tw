---
title: sync_per_container 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: d38307c4ae19e5f87d0dbcca8943dc1c3f239917
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232894"
---
# <a name="sync_per_container-class"></a>sync_per_container 類別

描述可為每個配置器物件提供不同快取物件的[同步處理篩選](../standard-library/allocators-header.md)。

## <a name="syntax"></a>語法

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*快取*|與同步處理篩選相關聯的快取類型。 這可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a>sync_per_container：： equals

比較兩個快取是否相等。

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*快取*|同步處理篩選的快取物件。|
|*其他*|要比較是否相等的快取物件。|

### <a name="return-value"></a>傳回值

成員函式一律會傳回 **`false`** 。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
