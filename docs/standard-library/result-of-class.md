---
title: result_of 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e05b8eb4352ca1556f8266dfc73247222583d4a8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="resultof-class"></a>result_of 類別

決定採用指定引數類型之可呼叫類型的傳回類型。

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

`Fn` 要查詢的可呼叫類型。

`ArgTypes` 要查詢的可呼叫類型的引數清單的類型。

## <a name="remarks"></a>備註

使用此樣板來判斷編譯時期 `Fn`(`ArgTypes`) 的結果類型，其中 `Fn` 是可呼叫的類型、函式的參考或可呼叫類型的參考，其是使用 `ArgTypes` 中類型的引數清單來叫用。 如果未經評估的運算式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正確，即會將樣板類別的 `type` 成員命名為 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的結果類型。 否則，樣板類別不會有 `type` 成員。 `Fn` 類型和參數封裝 `ArgTypes` 中的所有類型必須是完整類型、`void` 或界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
