---
title: invoke_result 類別
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: a5f67935bde103cf10c1bd9948ac1388f5221322
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473890"
---
# <a name="invoke_result-class"></a>invoke_result 類別

判斷在編譯時期接受指定引數類型之可呼叫類型的傳回類型。 已在 c + + 17 中新增。

## <a name="syntax"></a>語法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>參數

可呼叫*的\*
要查詢的可呼叫類型。

*Args*\
要查詢之可呼叫類型的引數清單類型。

## <a name="remarks"></a>備註

使用此範本在編譯時期判斷可呼叫（*Args*... *）的結果*類型 *，其中可呼叫的和* *args*中的所有類型都是任何完整的類型、未知系結的陣列，或可能是 cv 限定的 `void`。 類別樣板的 `type` 成員會在使用*arguments 自*變數來叫*用時，* 將可呼叫的傳回類型命名為。只有在*使用 arguments 自*變數來叫用時，*才會定義*`type` 成員 .。。在未計算的內容中。 否則，類別樣板沒有成員 `type`，這可讓您在編譯時期針對一組特定的引數類型進行 SFINAE 測試。

## <a name="requirements"></a>需求

**標頭：** \<type_traits >

**命名空間:** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
