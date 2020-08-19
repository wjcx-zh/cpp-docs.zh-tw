---
title: allocator_chunklist 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 64b419b2565609d8f6018facdbe25d5dee9d94aa
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562619"
---
# <a name="allocator_chunklist-class"></a>allocator_chunklist 類別

描述物件，該物件使用 [cache_chunklist](cache-chunklist-class.md) 類型的快取來管理物件的儲存空間配置和釋放。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>參數

*類型*\
配置器所配置的元素類型。

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會將這個類別傳遞為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
