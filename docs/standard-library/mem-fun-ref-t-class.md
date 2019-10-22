---
title: mem_fun_ref_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: d8f5ef05d1bdeec694cdf22d7e7a163478127dfc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687764"
---
# <a name="mem_fun_ref_t-class"></a>mem_fun_ref_t 類別

介面卡類別，允許在使用參考引數初始化時，不接受引數的 `non_const` 成員函式，當做一元函式物件來呼叫。 在 c + + 11 中已被取代，在 c + + 17 中移除

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;
};
```

### <a name="parameters"></a>參數

*_Pm* \
要轉換成函式物件之 `Type` 類別的成員函式指標。

*左方*\
呼叫 *_Pm*成員函式的物件。

## <a name="return-value"></a>傳回值

具適應性的一元函式。

## <a name="remarks"></a>備註

類別樣板會儲存 *_Pm*的複本，這必須是私用成員物件中 `Type` 類別之成員函式的指標。 它會將其成員函式 `operator()` 定義為傳回（**left**. * `_Pm`）（）。

## <a name="example"></a>範例

通常並不直接使用 `mem_fun_ref_t` 的建構函式，而協助程式函式 `mem_fun_ref` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)。
