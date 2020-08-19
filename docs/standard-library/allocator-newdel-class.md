---
title: allocator_newdel 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: 30e0f7902a8af435b46aaedf0b38661b7a6604a8
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562593"
---
# <a name="allocator_newdel-class"></a>allocator_newdel 類別

實作為配置器，使用 **operator delete** 來解除配置記憶體區塊和 **operator new** 來配置記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>參數

*類型*\
配置器所配置的元素類型。

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會將這個類別傳遞為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
