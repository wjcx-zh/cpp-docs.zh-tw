---
title: mem_fun1_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 822de97849750a72948137ba8fe23beab8554ff5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245081"
---
# <a name="memfun1t-class"></a>mem_fun1_t 類別

配接器類別，可讓`non_const`接受單一引數當做二元函式物件的指標引數初始化時要呼叫成員函式。 在 C + + 11 中，在 c++17 中移除已被取代。

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

*_Pm*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

*_Pleft*\
物件， *_Pm*上呼叫成員函式。

*權限*\
提供給引數 *_Pm*。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份 *_Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會定義其成員函式`operator()`做為傳回 ( **_Pleft** -> \* `_Pm`) (**右**)。

## <a name="example"></a>範例

通常並不直接使用 `mem_fun1_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。
