---
title: result_of 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95ac984ad164c242dcd470ed4d31f3921fa7ec56
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103262"
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

*fn*<br/>
要查詢的可呼叫類型。

*ArgTypes*<br/>
要查詢之可呼叫類型的引數清單類型。

## <a name="remarks"></a>備註

此範本可用來判斷在編譯時期的結果型別`Fn`(`ArgTypes`)，其中*Fn*是可呼叫的型別、 函式參考或可呼叫的型別，叫用中使用的類型引數清單的參考*ArgTypes*。 如果未經評估的運算式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` 格式正確，即會將樣板類別的 `type` 成員命名為 `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` 的結果類型。 否則，樣板類別不會有 `type` 成員。 型別*Fn*和參數的組件中的所有型別*ArgTypes*必須是完整類型**void**，或是界限未知的陣列。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
