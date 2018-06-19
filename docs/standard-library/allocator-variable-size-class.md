---
title: allocator_variable_size 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 690be271cd7e9ad3eaf019f1feb67202c14a9e5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840598"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size 類別

描述物件，該物件搭配使用 [cache_freelist](../standard-library/cache-freelist-class.md) 類型的快取與 [max_variable_size](../standard-library/max-variable-size-class.md) 所管理的長度，來管理 `Type` 類型之物件的儲存空間配置和釋放。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`Type`|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 巨集會將此類別傳遞為下列陳述式中的 `name` 參數：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
