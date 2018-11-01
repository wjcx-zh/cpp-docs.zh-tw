---
title: 多載一元運算子
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 802380bad59534e8402020142e394b3948032476
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497211"
---
# <a name="overloading-unary-operators"></a>多載一元運算子

可以多載的一元運算子如下：

1. `!` ([邏輯 NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([傳址](../cpp/address-of-operator-amp.md))

1. `~` ([一進位補數](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([指標取值 （dereference)](../cpp/indirection-operator-star.md))

1. `+` ([一元加號](../cpp/additive-operators-plus-and.md))

1. `-` ([一元否定運算](../cpp/additive-operators-plus-and.md))

1. `++` ([遞增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([遞減](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. 轉換運算子

後置遞增和遞減運算子 (`++`並`--`) 中需分開處理[遞增和遞減](../cpp/increment-and-decrement-operator-overloading-cpp.md)。

轉換運算子也會討論不同的主題。請參閱[使用者定義型別轉換](../cpp/user-defined-type-conversions-cpp.md)。

下列規則對於其他所有一元運算子皆成立。 若要將一元運算子函式宣告為非靜態成員，您必須以此格式進行宣告：

> *ret 型別***運算子** *op* **（)**

何處*ret 類型*是傳回的型別並*op*其中一個運算子會列在上表中。

若要將一元運算子函式宣告為全域函式，您必須以此格式進行宣告：

> *ret 型別***運算子** *op* **(** *arg* **)**

其中*ret 類型*並*op*成員運算子函式中所述， *arg*是所要執行的類別類型的引數。

> [!NOTE]
>  一元運算子的傳回型別沒有任何限制。 例如，邏輯 NOT (`!`) 傳回整數值是合理的，但不會強制執行。

## <a name="see-also"></a>另請參閱

[運算子多載](../cpp/operator-overloading.md)