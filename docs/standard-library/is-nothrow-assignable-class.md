---
title: is_nothrow_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 9ee8b5f97c92b6eb378db40f93696e5e6c554205
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456027"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable 類別

測試是否可以將*From*類型的值指派給類型 , 且已知指派不會擲回。

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>參數

*自*\
接收指派的物件類型。

*從*\
提供值的物件類型。

## <a name="remarks"></a>備註

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不會擲回。 *From*和*To*都必須是完整的類型、 **void**或未知系結的陣列。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
