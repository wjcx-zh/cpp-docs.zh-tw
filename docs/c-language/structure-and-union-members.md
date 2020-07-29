---
title: 結構和等位成員
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
ms.openlocfilehash: 70c89344e6afcdf52981f779c441c5ec47791a77
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211641"
---
# <a name="structure-and-union-members"></a>結構和等位成員

「成員選取運算式」(Member-selection Expression) 會參考結構和等位的成員。 這類運算式具有所選取成員的值和類型。

> 後置*運算式* **。** *標識*\
> 後置*運算式* **->***識別碼*

這個清單將描述兩種形式的成員選取運算式：

1. 在第一個表單中，後置*運算式*代表 **`struct`** 或類型的值 **`union`** ，而*identifier*會為指定結構或等位的成員命名。 運算的值會是 *identifier* 的值，而且如果 *postfix-expression* 為左值，運算的值也會是左值。 如需詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。

1. 在第二種形式中，*postfix-expression* 代表結構或等位的指標，而 *identifier* 會為所指定結構或等位的成員命名。 值會是 *identifier* 的值，而且是左值。

這兩種形式的成員選取運算式會產生類似的效果。

事實上， **->** 如果期間的運算式是由套用至指標值的間接取值運算子（）所組成，則牽涉到成員選取運算子（）的運算式就是使用句號（**.**）之運算式的速記版本 <strong>\*</strong> 。 因此，

```cpp
expression->identifier
```

相當於

```cpp
(*expression).identifier
```

(*expression* 為指標值時)。

## <a name="examples"></a>範例

下列範例會參考這個結構宣告。 如需這些範例中所使用間接取值運算子（）的相關資訊 <strong>\*</strong> ，請參閱[間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)。

```
struct pair
{
    int a;
    int b;
    struct pair *sp;
} item, list[10];
```

`item` 結構的成員選取運算式如下所示：

```
item.sp = &item;
```

在上面的範例中，`item` 結構的位址會指派給結構的 `sp` 成員。 這表示，`item` 包含本身的指標。

```
(item.sp)->a = 24;
```

在此範例中，指標運算式 `item.sp` 會搭配成員選取運算子（）使用， **->** 以將值指派給成員 `a` 。

```
list[8].b = 12;
```

這個陳述式將說明如何從結構陣列選取個別結構成員。

## <a name="see-also"></a>另請參閱

[成員存取運算子：. 和 ->](../cpp/member-access-operators-dot-and.md)
