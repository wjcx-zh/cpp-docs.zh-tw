---
title: result_of 類別
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 54806f965cc46058e3c82b4863bb45782abe079e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202307"
---
# <a name="result_of-class"></a>result_of 類別

決定採用指定引數類型之可呼叫類型的傳回類型。 已在 c + + 14 中新增，在 c + + 17 中被取代

## <a name="syntax"></a>語法

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>參數

*Fn*\
要查詢的可呼叫類型。

*ArgTypes*\
要查詢之可呼叫類型的引數清單類型。

## <a name="remarks"></a>備註

使用此範本在編譯時期判斷（）的結果類型 `Fn` `ArgTypes` ，其中*Fn*是可呼叫的類型、函式的參考或可呼叫類型的參考，並使用*ArgTypes*中類型的引數清單叫用。 `type` `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 如果未評估的運算式格式正確，類別樣板的成員會將的結果類型命名為 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 。 否則，類別樣板沒有成員 `type` 。 類型*Fn*和參數套件*ArgTypes*中的所有類型都必須是完整的類型、或未知系結 **`void`** 的陣列。 取代為 c + + 17 中的[invoke_result](invoke-result-class.md) 。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result 類別](invoke-result-class.md)
