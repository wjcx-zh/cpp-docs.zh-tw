---
title: allocator_unbounded 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: ba4c8b774752b327f5a4ede84fa804888cfd31d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617383"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded 類別

描述一個物件，它會使用類型[cache_freelist](cache-freelist-class.md)的快取來管理類型*類型*之物件的儲存空間配置和釋放，其長度是由[max_unbounded](max-unbounded-class.md)所管理。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會傳遞此類別做為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
