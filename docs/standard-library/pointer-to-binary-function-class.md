---
title: pointer_to_binary_function 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_binary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39549a277a203d9daa894f48437224caf50a0521
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853374"
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function 類別

將二元函式指標轉換成可調適性二元函式。

## <a name="syntax"></a>語法

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>參數

`pfunc` 要轉換將二元函式。

`left` 左物件 *\*pfunc*上呼叫。

`right` 右物件 *\*pfunc*上呼叫。

## <a name="return-value"></a>傳回值

此樣板類別會儲存 **pfunc** 的複本。 它會將其成員函式 `operator()`定義為傳回的 (\* **pfunc**)(_ *Left*, \_ *Right*)。

## <a name="remarks"></a>備註

二元函式指標是函式物件，可傳遞至預期二元函式做為參數的任何 C++ 標準程式庫演算法，但它不具可調適性。 若要使用它來搭配配接器 (例如與值繫結或使用它搭配否定運算子)，您都必須提供它能夠進行這類調適的巢狀類型：**first_argument_type**、**second_argument_type** 和 **result_type**。 透過 `pointer_to_binary_function` 的轉換可讓函式配接器使用二元函式指標。

## <a name="example"></a>範例

`pointer_to_binary_function` 的建構函式很少會直接使用。 如需如何宣告並使用 `pointer_to_binary_function` 配接器述詞的範例，請參閱協助程式函式 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
