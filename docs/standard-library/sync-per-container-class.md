---
title: sync_per_container 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 51a88e6ec4eca693c652635e1574e3611d7217cd
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562099"
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

*緩存*\
與同步處理篩選相關聯的快取類型。 它可以是 [`cache_chunklist`](../standard-library/cache-chunklist-class.md) 、 [`cache_freelist`](../standard-library/cache-freelist-class.md) 或 [`cache_suballoc`](../standard-library/cache-suballoc-class.md) 。

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[equals](#equals)|比較兩個快取是否相等。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a> sync_per_container：： equals

比較兩個快取是否相等。

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>參數

*緩存*\
同步處理篩選的快取物件。

*其他*\
要比較是否相等的快取物件。

### <a name="return-value"></a>傳回值

成員函式一律會傳回 **`false`** 。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
