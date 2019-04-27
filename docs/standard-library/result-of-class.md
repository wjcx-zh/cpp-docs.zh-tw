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
ms.openlocfilehash: f60a3ef6528da33fd1117fc940e961e9fe0987df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185902"
---
# <a name="resultof-class"></a>result_of 類別

決定採用指定引數類型之可呼叫類型的傳回類型。 新增在 c++14 中，在 c++17 中已被取代。

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

*fn*<br/>
要查詢的可呼叫類型。

*ArgTypes*<br/>
要查詢之可呼叫類型的引數清單類型。

## <a name="remarks"></a>備註

此範本可用來判斷在編譯時期的結果型別`Fn`(`ArgTypes`)，其中*Fn*是可呼叫的型別、 函式參考或可呼叫的型別，叫用中使用的類型引數清單的參考*ArgTypes*。 如果未經評估的運算式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正確，即會將樣板類別的 `type` 成員命名為 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的結果類型。 否則，樣板類別不會有 `type` 成員。 型別*Fn*和參數的組件中的所有型別*ArgTypes*必須是完整類型**void**，或是界限未知的陣列。 已被取代的益處[invoke_result](invoke-result-class.md)在 c++17 中。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke_result 類別](invoke-result-class.md)<br/>
