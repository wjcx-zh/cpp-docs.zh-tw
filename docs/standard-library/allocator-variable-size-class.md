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
ms.openlocfilehash: a2c4681ec5252166754a45b026ea119651f18a38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558917"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size 類別

描述物件，此物件可管理之類型的物件儲存體配置和釋放*型別*使用類型的快取[cache_freelist](../standard-library/cache-freelist-class.md)所管理的長度與[max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Type*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)巨集傳遞此類別做*名稱*下列陳述式中的參數： `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
