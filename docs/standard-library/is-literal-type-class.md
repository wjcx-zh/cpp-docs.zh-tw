---
title: is_literal_type 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456217"
---
# <a name="isliteraltype-class"></a>is_literal_type 類別

測試類型是否可用來作為 `constexpr` 變數，或是被 `constexpr` 函式建構、使用或傳回。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是*常數值型別*, 則類型述詞的實例為 true, 否則為 false。 常數值型別為**void**、純量類型、參考型別、常數值型別陣列或常值類別類型。 常值類別類型是一種擁有極簡解構函式的類別類型，它若不是匯總類型，就是至少有一個非移動、非複製 `constexpr` 建構函式，且其所有基底類別和非靜態資料成員都是非揮發性的常值類型。 雖然常值的類型一律是常值類型，但常值類型的概念還包括編譯器可在編譯階段評估為 `constexpr` 的任何項目。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
