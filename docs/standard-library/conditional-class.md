---
title: conditional 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: be81a1bc32f2f86f1d79970868933bddb8dc3620
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523015"
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

*B*<br/>
判斷這個選取之類型的值。

*T1*<br/>
B 為 true 時的類型結果。

*T2*<br/>
B 為 false 時的類型結果。

## <a name="remarks"></a>備註

範本成員 typedef`conditional<B, T1, T2>::type`評估為*T1*當*B*評估 **，則為 true**，並且判斷值為*T2*時*B*評估為**false**。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
