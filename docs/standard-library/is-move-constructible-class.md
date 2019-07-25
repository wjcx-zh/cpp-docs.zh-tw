---
title: is_move_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: c83ed4365fd0e73a7daa8b9894c5e85f20387a79
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456109"
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 類別

測試類型是否具有移動建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*而已*\
要評估的類型

## <a name="remarks"></a>備註

如果可以使用 move 作業來建立類型*T* , 則會評估為 true 的類型述詞。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
