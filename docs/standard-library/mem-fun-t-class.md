---
title: mem_fun_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 19ccd4835c4257a7f409bcf0f7bda1a898567458
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245092"
---
# <a name="memfunt-class"></a>mem_fun_t 類別

配接器類別，可讓`non_const`接受任何引數，當作一元函式物件的指標引數初始化時要呼叫成員函式。 在 C + + 11 中，在 c++17 中移除已被取代。

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>參數

*_Pm*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

*_Pleft*\
物件， *_Pm*上呼叫成員函式。

## <a name="return-value"></a>傳回值

具適應性的一元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份 *_Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會定義其成員函式`operator()`做為傳回 (`_Pleft`->* `_Pm`) （)。

## <a name="example"></a>範例

通常並不直接使用 `mem_fun_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。
