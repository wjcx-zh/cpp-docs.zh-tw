---
title: const_mem_fun_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 6b34fb6b20b2aaf2f18fbe8d937e50bdbaa3bdff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228345"
---
# <a name="const_mem_fun_t-class"></a>const_mem_fun_t 類別

配接器類別，這個類別允許不接受引數的常數成員函式在使用參考引數初始化時，可當做一元函式物件來呼叫。 在 c + + 11 中已被取代，在 c + + 17 中移除

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

*下午*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

*Pleft*\
呼叫*Pm*成員函式的物件。

## <a name="return-value"></a>傳回值

具適應性的一元函式。

## <a name="remarks"></a>備註

類別樣板會在私用成員物件中儲存*Pm*的複本，這必須是類別成員函式的指標 `Type` 。 它會將其成員函式定義 `operator()` 為傳回（ `Pleft` -> \* `Pm` ）（） **`const`** 。

## <a name="example"></a>範例

通常並不直接使用 `const_mem_fun_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。
