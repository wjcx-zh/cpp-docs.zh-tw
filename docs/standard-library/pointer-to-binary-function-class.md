---
title: pointer_to_binary_function 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 890ebb7d4c2b8fbd51a4460e21efba3e763ead7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687196"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function 類別

將二元函式指標轉換成可調適性二元函式。 在 c + + 11 中已被取代，在 c + + 17 中移除

## <a name="syntax"></a>語法

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>參數

*pfunc* \
要轉換的二元函式。

*左方*\
在其上呼叫 *\*pfunc* 的左側物件。

*right* \
在其上呼叫 *\*pfunc* 的右側物件。

## <a name="return-value"></a>傳回值

類別範本會儲存 `pfunc` 的複本。 它會將其成員函式 `operator()` 定義為傳回 `(* pfunc)(Left, right)`。

## <a name="remarks"></a>備註

二元函式指標是函式物件，可傳遞至預期二元函式做為參數的任何 C++ 標準程式庫演算法，但它不具可調適性。 若要搭配使用它與介面卡（例如，將值系結至其中，或與 negator 搭配使用），則必須提供 `first_argument_type`、`second_argument_type` 和 `result_type` 的巢狀型別，讓這類調整能夠進行。 透過 `pointer_to_binary_function` 的轉換可讓函式配接器使用二元函式指標。

## <a name="example"></a>範例

`pointer_to_binary_function` 的建構函式很少會直接使用。 如需如何宣告並使用 `pointer_to_binary_function` 配接器述詞的範例，請參閱協助程式函式 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。
