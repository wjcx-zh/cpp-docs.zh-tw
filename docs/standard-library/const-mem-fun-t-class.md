---
title: const_mem_fun_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 10a39d4b7871e08a5bf3ec56f6d11df5ad8b646c
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006457"
---
# <a name="constmemfunt-class"></a>const_mem_fun_t 類別

配接器類別，這個類別允許不接受引數的常數成員函式在使用參考引數初始化時，可當做一元函式物件來呼叫。 在 C + + 11 中，在 c++17 中移除已被取代。

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>參數

*Pm*<br/>
要轉換成函式物件之 `Type` 類別的成員函式指標。

*Pleft*<br/>
物件， *Pm*上呼叫成員函式。

## <a name="return-value"></a>傳回值

具適應性的一元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份*Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會在傳回下列項目時定義其成員函式 `operator()`：( `Pleft`->\* `Pm`)() **const**。

## <a name="example"></a>範例

通常並不直接使用 `const_mem_fun_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
