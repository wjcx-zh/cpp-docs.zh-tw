---
title: is_trivially_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 1f835dd348c6ef7f2ca7cd01f04c5afc059a55b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222325"
---
# <a name="is_trivially_constructible-class"></a>is_trivially_constructible 類別

測試類型在使用指定引數類型的情況下，是否是可透過極簡方式建構的類型。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

*引數*\
要在*T*的函式中符合的引數類型。

## <a name="remarks"></a>備註

如果類型*T*是使用*Args*中的引數類型完整可建構，則類型述詞的實例為 true，否則為 false。 如果*T*變數定義的 `T t(std::declval<Args>()...);` 格式正確，且已知不會呼叫任何非一般作業，則類型 T 會是完整可建構。 *參數*中的*T*和所有類型都必須是完整的類型、 **`void`** 或未知系結的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
