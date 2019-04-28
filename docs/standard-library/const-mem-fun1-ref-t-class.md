---
title: const_mem_fun1_ref_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 21d53178bf7ed80b5e0b170619e6221826393dab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212010"
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t 類別

配接器類別，這個類別可在使用參考引數初始化 **const** 成員函式 (其接受單一引數) 時，將其作為二元函式物件來呼叫。 在 C + + 11 中，在 c++17 中移除已被取代。

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
: public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>參數

*Pm*<br/>
要轉換成函式物件之 `Type` 類別的成員函式指標。

*left*<br/>
**Const**物件*Pm*上呼叫成員函式。

*right*<br/>
提供給引數*Pm*。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份*Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會在傳回下列項目時定義其成員函式 `operator()`：( `left`.\**Pm*)( `right`) **const**。

## <a name="example"></a>範例

`const_mem_fun1_ref_t` 的建構函式通常不會直接使用，而 helper 函式 `mem_fun_ref` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
