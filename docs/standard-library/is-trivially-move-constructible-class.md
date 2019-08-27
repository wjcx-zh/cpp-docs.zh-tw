---
title: is_trivially_move_constructible 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448367"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible 類別

測試類型是否有 trivial 移動建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果型別*Ty*是具有簡單的移動函式的類別, 則類型述詞的實例為 true, 否則為 false。

如果有下列情況, 類別*Ty*的移動函式就很簡單:

它是隱含宣告

其參數類型相等於隱含宣告的參數類型

類別*Ty*沒有虛擬函式

類別*Ty*沒有虛擬基底

類別沒有任何變動性的非靜態資料成員

類別*Ty*的所有直接基底都有簡單的移動函式

類別類型的所有非靜態資料成員的類別都具有 trivial 移動建構函式

類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 移動建構函式

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
