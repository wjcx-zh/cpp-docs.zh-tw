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
ms.openlocfilehash: 46ae9c613b66e00658f09ad10f33b721c6948ff7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456418"
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist 類別

描述物件，該物件使用 [cache_chunklist](../standard-library/cache-chunklist-class.md) 類型的快取來管理物件的儲存空間配置和釋放。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏會傳遞此類別作為下列語句中的*name*參數:`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
