---
title: is_literal_type 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: d5b750755f2499c89e91e497ed03244a11484871
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212250"
---
# <a name="is_literal_type-class"></a>is_literal_type 類別

測試類型是否可以做為變數使用， **`constexpr`** 或由函式來加以結構化、使用或傳回 **`constexpr`** 。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>參數

*而已*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*T*是*常數值型別*，則類型述詞的實例為 true，否則為 false。 常值型別可以是、純量 **`void`** 型別、參考型別、常值型別陣列，或 literal 類別型別。 常值類別類型是具有簡單的析構函式的類別類型，可以是匯總類型，或至少有一個非移動、非複製的程式 **`constexpr`** ，而且其所有基類和非靜態資料成員都是非 volatile 常數值型別。 雖然常值的類型一律是常數值型別，但常數值型別的概念包含編譯器可在編譯時期評估為的任何專案 **`constexpr`** 。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)
