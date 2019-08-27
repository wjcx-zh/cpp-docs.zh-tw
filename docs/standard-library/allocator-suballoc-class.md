---
title: allocator_suballoc 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 3e5b69ef3f47a173ef768283bbae4f6e3b5f5190
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458136"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc 類別

描述一個物件, 它會使用[cache_suballoc](../standard-library/cache-suballoc-class.md)類型的快取來管理類型*類型*物件的儲存空間配置和釋放。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)宏會傳遞此類別作為下列語句中的*name*參數:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
