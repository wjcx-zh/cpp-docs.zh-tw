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
ms.openlocfilehash: d49a1596371e4a69873b826d3e756f263539d034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448315"
---
# <a name="allocatornewdel-class"></a>allocator_newdel 類別

執行配置器, 它會使用**operator delete**來解除配置記憶體區塊, 並使用**new 運算子**來配置記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏會傳遞此類別作為下列語句中的*name*參數:`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
