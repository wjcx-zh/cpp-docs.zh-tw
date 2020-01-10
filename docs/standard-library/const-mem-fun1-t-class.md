---
title: const_mem_fun1_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 1af44635400037c6359b13c4f2925c3ac7f2d9d5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689756"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t 類別

配接器類別，這個類別可在使用指標引數初始化 **const** 成員函式 (其接受單一引數) 時，將其當作二元函式物件來呼叫。 在 c + + 11 中已被取代，在 c + + 17 中移除

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

*member_ptr* \
要轉換成函式物件之 `Type` 類別的成員函式指標。

*左方*\
呼叫*member_ptr*成員函式的**const**物件。

*right* \
要提供給*member_ptr*的引數。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

類別樣板會儲存*member_ptr*的複本，這必須是私用成員物件中 `Type` 類別之成員函式的指標。 它會將其成員函式 `operator()` 定義為傳回 `(left->member_ptr)(right) const`。

## <a name="example"></a>範例

`const_mem_fun1_t` 的建構函式很少會直接使用。 `mem_fn` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱[mem_fn](../standard-library/functional-functions.md#mem_fn) 。
