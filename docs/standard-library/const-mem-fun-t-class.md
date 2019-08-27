---
title: const_mem_fun_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 0bdfdbac7a23a4b0e3b830b05990bf028c7bb316
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244552"
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

*Pm*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

*Pleft*\
物件， *Pm*上呼叫成員函式。

## <a name="return-value"></a>傳回值

具適應性的一元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份*Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會定義其成員函式`operator()`做為傳回 (`Pleft` -> \* `Pm`) （) **const**。

## <a name="example"></a>範例

通常並不直接使用 `const_mem_fun_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。
