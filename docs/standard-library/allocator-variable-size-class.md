---
title: allocator_variable_size 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: 4e4c5ab0167d49c9ee892f39f18892edd004c3f6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623709"
---
# <a name="allocator_variable_size-class"></a>allocator_variable_size 類別

描述一個物件，它會使用類型[cache_freelist](cache-freelist-class.md)的快取來管理類型*類型*之物件的儲存空間配置和釋放，其長度是由[max_variable_size](max-variable-size-class.md)所管理。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)宏會傳遞此類別做為下列語句中的*name*參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
