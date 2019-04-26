---
title: allocator_unbounded 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 4e5bf54b386a3c3fe4e2604a78437275707acbfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179174"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded 類別

描述物件，此物件可管理之類型的物件儲存體配置和釋放*型別*使用類型的快取[cache_freelist](../standard-library/cache-freelist-class.md)所管理的長度與[max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>語法

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Type*|配置器所配置的元素類型。|

## <a name="remarks"></a>備註

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)巨集傳遞此類別做*名稱*下列陳述式中的參數： `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
