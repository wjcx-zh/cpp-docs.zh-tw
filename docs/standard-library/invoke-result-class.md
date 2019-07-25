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
ms.openlocfilehash: 2b2051b0c854151cff9b439f5ec0a951c25a6387
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447633"
---
# <a name="invokeresult-class"></a>invoke_result 類別

判斷在編譯時期接受指定引數類型之可呼叫類型的傳回類型。 已在 c + + 17 中新增。

## <a name="syntax"></a>語法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>參數

*多次*\
要查詢的可呼叫類型。

*引數*\
要查詢之可呼叫類型的引數清單類型。

## <a name="remarks"></a>備註

使用此範本在編譯時期判斷可呼叫(*Args*...) 的結果類型, 其中可呼叫的和*args*中的所有類型都是任何完整的類型、未知系結的陣列, 或可能是 cv `void`限定的。 樣板`type`類別的成員會在使用 arguments 引數來叫用時, 將可呼叫的傳回類型命名為。只有在使用 arguments 引數來叫用時, 才會定義成員...`type`在未計算的內容中。 否則, 樣板類別沒有成員`type`, 可讓您在編譯時期針對一組特定的引數類型進行 SFINAE 測試。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
