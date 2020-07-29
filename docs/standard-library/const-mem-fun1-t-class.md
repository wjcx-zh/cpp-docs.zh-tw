---
title: const_mem_fun1_t 類別
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 93d0e7a116c7c7ba7a2ed1cb46fd88585a99120d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228319"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t 類別

介面卡類別，允許在 **`const`** 使用指標引數初始化時，接受單一引數的成員函式當做二元函式物件來呼叫。 在 c + + 11 中已被取代，在 c + + 17 中移除

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

*member_ptr*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

*左面*\
要 **`const`** 在其上呼叫*member_ptr*成員函式的物件。

*再*\
為*member_ptr*所提供的引數。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

類別樣板會在私用成員物件中儲存*member_ptr*的複本，這必須是類別成員函式的指標 `Type` 。 它會將其成員函式定義 `operator()` 為傳回 `(left->member_ptr)(right) const` 。

## <a name="example"></a>範例

`const_mem_fun1_t` 建構函式很少會直接使用。 `mem_fn`是用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱[mem_fn](../standard-library/functional-functions.md#mem_fn) 。
