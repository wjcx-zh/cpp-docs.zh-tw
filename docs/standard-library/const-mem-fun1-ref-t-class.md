---
title: const_mem_fun1_ref_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 76fae1ce29cb4c47870e45e8f946f6ff1fea1885
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688181"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t 類別

配接器類別，這個類別可在使用參考引數初始化 **const** 成員函式 (其接受單一引數) 時，將其作為二元函式物件來呼叫。 在 c + + 11 中已被取代，在 c + + 17 中移除

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

*Pm* \
要轉換成函式物件之 `Type` 類別的成員函式指標。

*左方*\
呼叫*Pm*成員函式的**常數**物件。

*right* \
要提供給*Pm*的引數。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

類別樣板會儲存*Pm*的複本，這必須是私用成員物件中，`Type` 類別之成員函式的指標。 它會將其成員函式 `operator()` 定義為傳回（`left` \* *Pm*）（`right`） **const**。

## <a name="example"></a>範例

通常並不直接使用 `const_mem_fun1_ref_t` 的建構函式，而協助程式函式 `mem_fun_ref` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。
