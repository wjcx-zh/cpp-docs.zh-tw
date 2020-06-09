---
title: allocator_suballoc 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 01d282585133d55ee3f7ec96c212705c2afca9d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617430"
---
# <a name="allocator_suballoc-class"></a>allocator_suballoc 類別

描述一個物件，它會使用[cache_suballoc](cache-suballoc-class.md)類型的快取來管理類型*類型*物件的儲存空間配置和釋放。

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

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會傳遞此類別做為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
