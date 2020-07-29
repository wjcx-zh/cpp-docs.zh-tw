---
title: is_nothrow_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 7130079ff58820ec5a8893fd248c5b98fc10c93c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222364"
---
# <a name="is_nothrow_assignable-class"></a>is_nothrow_assignable 類別

測試是否可以將*From*類型的值指派*給類型，* 且已知指派不會擲回。

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

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不會擲回。 *From*和*To*都必須是完整的類型、或未知系結 **`void`** 的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
