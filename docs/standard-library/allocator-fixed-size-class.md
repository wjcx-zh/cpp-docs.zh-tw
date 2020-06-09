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
ms.openlocfilehash: 124c49b22566e44989fd30a3274c2d121532eef4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617484"
---
# <a name="allocator_fixed_size-class"></a>allocator_fixed_size 類別

描述一個物件，它會使用類型[cache_freelist](cache-freelist-class.md)的快取來管理類型*類型*之物件的儲存空間配置和釋放，其長度是由[max_fixed_size](max-fixed-size-class.md)所管理。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會傳遞此類別做為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
