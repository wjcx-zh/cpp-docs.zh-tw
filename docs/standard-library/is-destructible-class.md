---
title: is_destructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: cd3c54684fe08a77d3a8774cd6a2554db9fb0c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215682"
---
# <a name="is_destructible-class"></a>is_destructible 類別

測試類型是否為易損壞的。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是易損壞類型，則類型述詞的實例為 true，否則為 false。 易損壞的類型是指參考類型、物件類型和類型，其中某些類型的 `U` 等於 `remove_all_extents_t<T>` ，且未經過評估的運算元 `std::declval<U&>.~U()` 是語式正確的。 其他類型（包括不完整的類型、和函式 **`void`** 類型）不是易損壞類型。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
