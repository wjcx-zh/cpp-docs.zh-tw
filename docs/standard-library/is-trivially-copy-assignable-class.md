---
title: is_trivially_copy_assignable 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: c0019257a032d3becc268513336ed59e58a2e1d5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448002"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable 類別

測試類型是否有 trivial 複製指派運算子。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是具有簡單複製指派運算子的類別, 則類型述詞的實例為 true, 否則為 false。

類別*t*的指派函式若隱含提供, 則為不常用, 類別*t*沒有虛擬函數, 類別*t*沒有虛擬基底, 類別類型的所有非靜態資料成員的類別都有簡單的指派運算子, 以及類別之類型陣列的所有非靜態資料成員的類別, 都具有簡單的指派運算子。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
