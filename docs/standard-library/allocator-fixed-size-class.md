---
title: allocator_fixed_size 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94207895eb88e0d799289e2c730f99668ca32cef
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963192"
---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size 類別

描述物件，此物件可管理之類型的物件儲存體配置和釋放*型別*使用類型的快取[cache_freelist](../standard-library/cache-freelist-class.md)所管理的長度與[max_fixed_size](../standard-library/max-fixed-size-class.md).

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*類型*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)巨集傳遞此類別做*名稱*下列陳述式中的參數： `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
