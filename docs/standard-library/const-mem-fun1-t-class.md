---
title: const_mem_fun1_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: df984d90f8b632f8e3e3b183943343952d45b8be
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006353"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t 類別

配接器類別，這個類別可在使用指標引數初始化 **const** 成員函式 (其接受單一引數) 時，將其當作二元函式物件來呼叫。 在 C + + 11 中，在 c++17 中移除已被取代。

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>參數

*member_ptr*<br/>
要轉換成函式物件之 `Type` 類別的成員函式指標。

*left*<br/>
**Const**物件*member_ptr*上呼叫成員函式。

*right*<br/>
提供給引數*member_ptr*。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份*member_ptr*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會定義其成員函式`operator()`做為傳回`(left->member_ptr)(right) const`。

## <a name="example"></a>範例

`const_mem_fun1_t` 的建構函式很少會直接使用。 `mem_fn` 用來調整成員函式。 請參閱[mem_fn](../standard-library/functional-functions.md#mem_fn)如需如何使用成員函式配接器的範例。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
