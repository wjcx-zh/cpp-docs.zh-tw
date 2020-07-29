---
title: is_trivially_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 14a3ee638bd6df3b52e7327ca6e3c77f4a0e8b71
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224860"
---
# <a name="is_trivially_assignable-class"></a>is_trivially_assignable 類別

測試是否可將 `From` 類型的值透過極簡方式指派給 `To` 類型

## <a name="syntax"></a>語法

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>參數

*自*\
接收指派的物件類型。

*從*\
提供值的物件類型。

## <a name="remarks"></a>備註

運算式 `declval<To>() = declval<From>()` 必須格式正確，且編譯器必須已知它不需要任何非極簡作業。 `From`和都 `To` 必須是完整的類型、 **`void`** 或未知系結的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
