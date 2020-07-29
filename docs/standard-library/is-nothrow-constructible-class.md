---
title: is_nothrow_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: e52b16965d849f992731c4ff4254fd218b944269
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217749"
---
# <a name="is_nothrow_constructible-class"></a>is_nothrow_constructible 類別

測試當使用指定的引數類型時，類型是否是可建構的類型且已知不會擲回。

## <a name="syntax"></a>語法

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

*引數*\
要在*T*的函式中符合的引數類型。

## <a name="remarks"></a>備註

如果使用*Args*中的引數類型來可建構類型*T* ，而且編譯器知道此函式不會擲回，則類型述詞的實例會保留 true;否則會保留 false。 如果變數定義的格式正確，類型*T*就會可建構 `T t(std::declval<Args>()...);` 。 *參數*中的*T*和所有類型都必須是完整的類型、 **`void`** 或未知系結的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
