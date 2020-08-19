---
title: allocator_unbounded 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: d9d82dd29ab86654020e13b39a8c9588ee0732e8
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561540"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded 類別

描述物件，此物件 *會使用類型* [cache_freelist](cache-freelist-class.md) 的快取來管理類型為類型之物件的儲存配置和釋出，其長度由 [max_unbounded](max-unbounded-class.md)管理。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>參數

*類型*\
配置器所配置的元素類型。

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會將這個類別傳遞為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
