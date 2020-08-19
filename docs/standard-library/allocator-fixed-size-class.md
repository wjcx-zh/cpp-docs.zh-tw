---
title: allocator_fixed_size 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
ms.openlocfilehash: 340a4e51c82f1799ebea138ce230393825b9e636
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562606"
---
# <a name="allocator_fixed_size-class"></a>allocator_fixed_size 類別

描述物件，此物件 *會使用類型* [cache_freelist](cache-freelist-class.md) 的快取來管理類型為類型之物件的儲存配置和釋出，其長度由 [max_fixed_size](max-fixed-size-class.md)管理。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>參數

*類型*\
配置器所配置的元素類型。

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會將這個類別傳遞為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
