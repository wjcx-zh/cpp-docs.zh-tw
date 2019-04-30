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
ms.openlocfilehash: 7c03240d3ee666fcda30562279a8dbda2ca8dc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404842"
---
# <a name="invokeresult-class"></a>invoke_result 類別

判斷在編譯時期會取得指定的引數類型的可呼叫類型的傳回型別。 在 C + + 17 中新增。

## <a name="syntax"></a>語法

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>參數

*Callable*<br/>
要查詢的可呼叫類型。

*Args*<br/>
要查詢之可呼叫類型的引數清單類型。

## <a name="remarks"></a>備註

此範本可用來判斷的結果型別*Callable*(*Args*...) 在編譯時期，其中*Callable*和中的所有型別*Args*為任何完整的型別、 未知的繫結的陣列，或可能是 cv 限定`void`。 `type`範本類別的成員名稱的傳回型別*Callable*時使用的引數叫用*Args*...`type`如果只定義成員*Callable*狀態時使用的引數叫用呼叫*Args*...中的未評估的內容。 否則，此範本類別沒有任何成員`type`，可讓 SFINAE 上一組特定的引數型別測試，在編譯時期。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)
