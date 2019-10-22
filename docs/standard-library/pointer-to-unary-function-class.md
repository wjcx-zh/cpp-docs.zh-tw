---
title: pointer_to_unary_function 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 2b6bf82faa39e22c5af584a9fc3ebf68f5851463
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689133"
---
# <a name="pointer_to_unary_function-class"></a>pointer_to_unary_function 類別

將一元函式指標轉換成可調適性一元函式。 在 c + + 11 中已被取代，在 c + + 17 中移除

## <a name="syntax"></a>語法

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>參數

*pfunc* \
要轉換的二元函式。

*左方*\
在其上呼叫 *\*pfunc* 的物件。

## <a name="return-value"></a>傳回值

類別範本會儲存 `pfunc` 的複本。 它會在傳回 (\* **pfunc**)(_ *Left*) 時定義其成員函式 `operator()`。

## <a name="remarks"></a>備註

一元函式指標是函式物件，可傳遞至需要一元函式當作參數的任何 C++ 標準程式庫演算法，但它不具可調適性。 若要將它與介面卡搭配使用，例如將值系結至它或與 negator 搭配使用，則必須提供 `argument_type` 和 `result_type` 的巢狀型別，以進行這類調整。 透過 `pointer_to_unary_function` 的轉換可讓函式配接器使用二元函式指標。

## <a name="example"></a>範例

`pointer_to_unary_function` 的建構函式很少會直接使用。 如需如何宣告並使用 `pointer_to_unary_function` 配接器述詞的範例，請參閱協助程式函式 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。
