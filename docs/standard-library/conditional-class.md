---
title: conditional 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: b8f0f69cc1e4f6966bc9ccb63fe529436295badd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457317"
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

\
B 為 false 時的類型結果。

## <a name="remarks"></a>備註

當*b*評估為`conditional<B, T1, T2>::type` **true**時, 範本成員 typedef 會評估為*T1* , 而當*b*評估為**false**時, 則評估為*T2* 。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
