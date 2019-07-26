---
title: is_trivially_move_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 324e4a1f1bd3528f09f21c5e485ac814038b7517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448374"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 類別

測試類型是否有 trivial 移動指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是具有簡單的移動指派運算子的類別, 則類型述詞的實例為 true, 否則為 false。

*Ty*類別的移動指派運算子在下列情況中是很簡單的:

它會隱含地提供

類別*Ty*沒有虛擬函式

類別*Ty*沒有虛擬基底

類別類型的所有非靜態資料成員的類別具有 trivial 移動指派運算子

類別的類型陣列的所有非靜態資料成員的類別具有 trivial 移動指派運算子

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
