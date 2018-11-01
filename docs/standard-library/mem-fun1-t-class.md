---
title: mem_fun1_t 類別
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 9a1fe26e66eb2ad20e6889b95640fadd2b3c45a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613187"
---
# <a name="memfun1t-class"></a>mem_fun1_t 類別

配接器類別，可讓`non_const`接受單一引數當做二元函式物件的指標引數初始化時要呼叫成員函式。

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

};
```

### <a name="parameters"></a>參數

*_Pm*<br/>
要轉換成函式物件之 `Type` 類別的成員函式指標。

*_Pleft*<br/>
物件， *_Pm*上呼叫成員函式。

*right*<br/>
提供給引數 *_Pm*。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份 *_Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會將其成員函式 `operator()` 定義為傳回 ( **_Pleft**->\* `_Pm`)( **right**)。

## <a name="example"></a>範例

通常並不直接使用 `mem_fun1_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
