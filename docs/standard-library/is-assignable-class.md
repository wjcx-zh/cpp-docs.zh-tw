---
title: is_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 33b0ce6112119c935ff70e5d619b284acc6ee8c2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456674"
---
# <a name="isassignable-class"></a>is_assignable 類別

測試是否可將 `From` 類型的值指派給 `To` 類型。

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>參數

*自*\
接收指派的物件類型。

*從*\
提供值的物件類型。

## <a name="remarks"></a>備註

未評估的運算式 `declval<To>() = declval<From>()` 必須格式正確。 和`From` 都`To`必須是完整的類型、 **void**或未知系結的陣列。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
