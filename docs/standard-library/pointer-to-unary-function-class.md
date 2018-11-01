---
title: pointer_to_unary_function 類別
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: dc8a324d27870f615b810a3e86c355fadaf5c78d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558323"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function 類別

將一元函式指標轉換成可調適性一元函式。

## <a name="syntax"></a>語法

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>參數

*pfunc*<br/>
要轉換的二元函式。

*left*<br/>
在其上呼叫 *\*pfunc* 的物件。

## <a name="return-value"></a>傳回值

此範本類別會儲存一份`pfunc`。 它會在傳回 (\* **pfunc**)(_ *Left*) 時定義其成員函式 `operator()`。

## <a name="remarks"></a>備註

一元函式指標是函式物件，可傳遞至需要一元函式當作參數的任何 C++ 標準程式庫演算法，但它不具可調適性。 若要使用它來搭配配接器，例如與值繫結到它，或使用它搭配否定，它必須提供的巢狀類型`argument_type`和`result_type`，進行這類調適。 透過 `pointer_to_unary_function` 的轉換可讓函式配接器使用二元函式指標。

## <a name="example"></a>範例

`pointer_to_unary_function` 的建構函式很少會直接使用。 如需如何宣告並使用 `pointer_to_unary_function` 配接器述詞的範例，請參閱協助程式函式 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
