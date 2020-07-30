---
title: conditional 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: 03ec6248ba3361622ad061ac3854a60995148f4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228371"
---
# <a name="conditional-class"></a>conditional 類別

根據指定的條件選取這兩種類型之一。

## <a name="syntax"></a>語法

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>參數

*位元組*\
判斷這個選取之類型的值。

*T1*\
B 為 true 時的類型結果。

*T2*\
B 為 false 時的類型結果。

## <a name="remarks"></a>備註

當 b `conditional<B, T1, T2>::type` 評估為時，範本成員*B* typedef 會評估為*T1* **`true`** ，而當*b*評估為時，會評估為*T2* **`false`** 。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
