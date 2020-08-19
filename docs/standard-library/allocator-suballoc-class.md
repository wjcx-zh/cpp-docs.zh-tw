---
title: allocator_suballoc 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 47b82a198a52a61bd5558bd59a38b1d328fa67b2
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562580"
---
# <a name="allocator_suballoc-class"></a>allocator_suballoc 類別

描述物件，該物件會使用[cache_suballoc](cache-suballoc-class.md)類型的快取來管理*類型類型物件*的儲存配置和釋放。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>參數

*類型*\
配置器所配置的元素類型。

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會將這個類別傳遞為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
