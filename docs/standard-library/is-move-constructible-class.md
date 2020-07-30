---
title: is_move_constructible 類別
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 5495ac39a98f5c194f19d28ba85a1d59f47dfbb4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222377"
---
# <a name="is_move_constructible-class"></a>is_move_constructible 類別

測試類型是否可以使用移動作業來建立。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*而已*\
要評估的類型。

## <a name="remarks"></a>備註

**`true`** 如果類型*T*可以使用移動作業來建立，則會評估為的類型述詞。 這個述詞相當於 `is_constructible<T, T&&>`。 不具有移動函數的類型*T* ，但有可接受引數的複製函式 `const T&` （滿足） `std::is_move_constructible` 。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
