---
title: is_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: a968efa5a867a3fd0e60594784cdb11122a974b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222403"
---
# <a name="is_constructible-class"></a>is_constructible 類別

測試當使用指定的引數類型時，類型是否是可建構的類型。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

*引數*\
要在*T*的函式中符合的引數類型。

## <a name="remarks"></a>備註

如果類型*T*是使用*Args*中的引數類型來可建構，則類型述詞的實例為 true，否則為 false。 如果變數定義的格式正確，類型*T*就會可建構 `T t(std::declval<Args>()...);` 。 *參數*中的*T*和所有類型都必須是完整的類型、 **`void`** 或未知系結的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
