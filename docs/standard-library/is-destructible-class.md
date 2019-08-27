---
title: is_destructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 80592a6fca274533a798b2f5a2459d336ee2c301
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452738"
---
# <a name="isdestructible-class"></a>is_destructible 類別

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

如果類型*T*是易損壞類型, 則類型述詞的實例為 true, 否則為 false。 易損壞的類型是指參考類型、物件類型和類型，其中某些類型的 `U` 等於 `remove_all_extents_t<T>` ，且未經過評估的運算元 `std::declval<U&>.~U()` 是語式正確的。 其他類型 (包括不完整的類型、 **void**和函式類型) 則不是易損壞類型。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
