---
title: pointer_to_unary_function 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: cff84f1f15eea34c60162f702dfe05350d1383d1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240461"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function 類別

將一元函式指標轉換成可調適性一元函式。 在 C + + 11 中，在 c++17 中移除已被取代。

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

*pfunc*\
要轉換的二元函式。

*左邊*\
在其上呼叫 *\*pfunc* 的物件。

## <a name="return-value"></a>傳回值

此範本類別會儲存一份`pfunc`。 它會在傳回 (\* **pfunc**)(_ *Left*) 時定義其成員函式 `operator()`。

## <a name="remarks"></a>備註

一元函式指標是函式物件，可傳遞至需要一元函式當作參數的任何 C++ 標準程式庫演算法，但它不具可調適性。 若要使用它來搭配配接器，例如與值繫結到它，或使用它搭配否定，它必須提供的巢狀類型`argument_type`和`result_type`，進行這類調適。 透過 `pointer_to_unary_function` 的轉換可讓函式配接器使用二元函式指標。

## <a name="example"></a>範例

`pointer_to_unary_function` 的建構函式很少會直接使用。 如需如何宣告並使用 `pointer_to_unary_function` 配接器述詞的範例，請參閱協助程式函式 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。
