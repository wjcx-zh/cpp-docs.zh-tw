---
title: allocator_suballoc 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
dev_langs:
- C++
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6238aeada530a8fc33fc98b79cba969353796ae
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953084"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc 類別

描述物件，此物件可管理之類型的物件儲存體配置和釋放*型別*使用類型的快取[cache_suballoc](../standard-library/cache-suballoc-class.md)。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*類型*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)巨集傳遞此類別做*名稱*下列陳述式中的參數： `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
