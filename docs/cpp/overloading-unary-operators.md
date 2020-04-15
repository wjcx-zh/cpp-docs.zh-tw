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
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372037"
---
# <a name="overloading-unary-operators"></a>多載一元運算子

可以多載的一元運算子如下：

1. `!`([邏輯不](../cpp/logical-negation-operator-exclpt.md))

1. `&`([位址](../cpp/address-of-operator-amp.md))

1. `~`([一個人的修補品](../cpp/one-s-complement-operator-tilde.md))

1. `*`([指標取消參考](../cpp/indirection-operator-star.md))

1. `+`([一元加](../cpp/additive-operators-plus-and.md))

1. `-`([一元否定](../cpp/additive-operators-plus-and.md))

1. `++`([增量](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([減分](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. 轉換運算子

後綴增量和遞減運算符(`++`和`--`) 以[增量和遞減](../cpp/increment-and-decrement-operator-overloading-cpp.md)分別處理。

轉換運算符也在單獨的主題中討論;請參考[使用者定義的類型轉換](../cpp/user-defined-type-conversions-cpp.md)。

下列規則對於其他所有一元運算子皆成立。 若要將一元運算子函式宣告為非靜態成員，您必須以此格式進行宣告：

> *ret 型***運算子***操作* **()**

其中*ret 類型*是傳回類型,*操作*是上表中列出的運算符之一。

若要將一元運算子函式宣告為全域函式，您必須以此格式進行宣告：

> *ret 型***運算子** *op* **(** *arg* **)**

其中*ret 類型*和*op*與成員運算符函數的描述相同 *,arg*是要操作的類類型的參數。

> [!NOTE]
> 一元運算子的傳回型別沒有任何限制。 例如，邏輯 NOT (`!`) 傳回整數值是合理的，但不會強制執行。

## <a name="see-also"></a>另請參閱

[操作員重載](../cpp/operator-overloading.md)
