---
title: is_move_constructible 類別
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920095"
---
# <a name="is_move_constructible-class"></a>is_move_constructible 類別

測試類型是否可以使用移動作業來建立。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*T* \
要評估的類型。

## <a name="remarks"></a>備註

如果可以使用 move 作業來建立類型*T* ，則會評估為**true**的類型述詞。 這個述詞相當於 `is_constructible<T, T&&>`。 型*別 T*沒有移動的函式，但有可接受 `const T&` 引數的複製程式，以滿足 `std::is_move_constructible`。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間:** std

## <a name="see-also"></a>請參閱

[<type_traits>](../standard-library/type-traits.md)
