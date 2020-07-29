---
title: C + + 內建運算子、優先順序和關聯性
ms.date: 07/23/2020
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: 10c9e5db569ba211ed8d42386816b4f6bb71ee29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221766"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C + + 內建運算子、優先順序和關聯性

C++ 語言包含所有 C 運算子，並且新增了數個新的運算子。 運算子指定要對一個或多個運算元執行的評估：

## <a name="precedence-and-associativity"></a>優先順序和關聯性

運算子*優先順序*：指定運算式中包含多個運算子的作業順序。 運算子*關聯*性：指定在包含多個具有相同優先順序之運算子的運算式中，運算元會群組在其左邊或其右邊的一個。

## <a name="alternative-spellings"></a>替代拼寫

C + + 為某些運算子指定替代的拼寫。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，這些替代專案是關鍵字，使用 \<iso646.h> 或 c + + 對等專案 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="c-operator-precedence-and-associativity-table"></a>C + + 運算子優先順序和關聯性資料表

下表顯示 C++ 運算子的優先順序和順序關聯性 (從最高到最低優先順序)。 除非以括號明確強制其他關聯性，否則運算子的優先順序數字若相同，其優先順序即相等。

| 運算子描述 | 運算子 | 替代函式 |
|--|--|--|
| **群組1優先順序，無關聯性** |
| [範圍解析](../cpp/scope-resolution-operator.md) | [`::`](../cpp/scope-resolution-operator.md) |
| **群組2優先順序，從左至右的關聯性** |
| [成員選取 (物件或指標)](../cpp/member-access-operators-dot-and.md) | [`.`或`->`](../cpp/member-access-operators-dot-and.md) |
| [陣列註標](../cpp/subscript-operator.md) | [`[]`](../cpp/subscript-operator.md) |
| [函式呼叫](../cpp/function-call-operator-parens.md) | [`()`](../cpp/function-call-operator-parens.md) |
| [後置遞增](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [後置遞減](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md) |
| [類型名稱](../cpp/typeid-operator.md) | [`typeid`](../cpp/typeid-operator.md) |
| [常數類型轉換](../cpp/const-cast-operator.md) | [`const_cast`](../cpp/const-cast-operator.md) |
| [動態類型轉換](../cpp/dynamic-cast-operator.md) | [`dynamic_cast`](../cpp/dynamic-cast-operator.md) |
| [重新轉譯的類型轉換](../cpp/reinterpret-cast-operator.md) | [`reinterpret_cast`](../cpp/reinterpret-cast-operator.md) |
| [靜態類型轉換](../cpp/static-cast-operator.md) | [`static_cast`](../cpp/static-cast-operator.md) |
| **群組3優先順序，由右至左關聯性** |
| [物件或類型的大小](../cpp/sizeof-operator.md) | [`sizeof`](../cpp/sizeof-operator.md) |
| [前置遞增](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`++`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [前置遞減](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) | [`--`](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md) |
| [一補數](../cpp/one-s-complement-operator-tilde.md) | [`~`](../cpp/one-s-complement-operator-tilde.md) | **`compl`** |
| [邏輯 not](../cpp/logical-negation-operator-exclpt.md) | [`!`](../cpp/logical-negation-operator-exclpt.md) | **`not`** |
| [一元負運算](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`-`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [一元加號](../cpp/unary-plus-and-negation-operators-plus-and.md) | [`+`](../cpp/unary-plus-and-negation-operators-plus-and.md) |
| [傳址](../cpp/address-of-operator-amp.md) | [`&`](../cpp/address-of-operator-amp.md) |
| [間接](../cpp/indirection-operator-star.md) | [`*`](../cpp/indirection-operator-star.md) |
| [建立物件](../cpp/new-operator-cpp.md) | [`new`](../cpp/new-operator-cpp.md) |
| [終結物件](../cpp/delete-operator-cpp.md) | [`delete`](../cpp/delete-operator-cpp.md) |
| [鑄造](../cpp/cast-operator-parens.md) | [`()`](../cpp/cast-operator-parens.md) |
| **群組4優先順序，從左至右的關聯性** |
| [成員指標 (物件或指標)](../cpp/pointer-to-member-operators-dot-star-and-star.md) | [`.*`或`->*`](../cpp/pointer-to-member-operators-dot-star-and-star.md) |
| **群組5優先順序，從左至右的關聯性** |
| [乘](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`*`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [部門](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`/`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| [模組](../cpp/multiplicative-operators-and-the-modulus-operator.md) | [`%`](../cpp/multiplicative-operators-and-the-modulus-operator.md) |
| **群組6優先順序，從左至右的關聯性** |
| [加法](../cpp/additive-operators-plus-and.md) | [`+`](../cpp/additive-operators-plus-and.md) |
| [減](../cpp/additive-operators-plus-and.md) | [`-`](../cpp/additive-operators-plus-and.md) |
| **群組7優先順序，從左至右的關聯性** |
| [左移](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`<<`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| [右移](../cpp/left-shift-and-right-shift-operators-input-and-output.md) | [`>>`](../cpp/left-shift-and-right-shift-operators-input-and-output.md) |
| **群組8優先順序，從左至右的關聯性** |
| [小於](../cpp/relational-operators-equal-and-equal.md) | [`<`](../cpp/relational-operators-equal-and-equal.md) |
| [大於](../cpp/relational-operators-equal-and-equal.md) | [`>`](../cpp/relational-operators-equal-and-equal.md) |
| [小於或等於](../cpp/relational-operators-equal-and-equal.md) | [`<=`](../cpp/relational-operators-equal-and-equal.md) |
| [大於或等於](../cpp/relational-operators-equal-and-equal.md) | [`>=`](../cpp/relational-operators-equal-and-equal.md) |
| **群組9優先順序，從左至右的關聯性** |
| [等式](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`==`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) |
| [不等](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | [`!=`](../cpp/equality-operators-equal-equal-and-exclpt-equal.md) | **`not_eq`** |
| **群組10優先順序留給右關聯性** |
| [位元 AND](../cpp/bitwise-and-operator-amp.md) | [`&`](../cpp/bitwise-and-operator-amp.md) | **`bitand`** |
| **群組11優先順序，從左至右的關聯性** |
| [位元排除 OR](../cpp/bitwise-exclusive-or-operator-hat.md) | [`^`](../cpp/bitwise-exclusive-or-operator-hat.md) | **`xor`** |
| **群組12優先順序，從左至右的關聯性** |
| [位元包含 OR](../cpp/bitwise-inclusive-or-operator-pipe.md) | [`|`](../cpp/bitwise-inclusive-or-operator-pipe.md) | **`bitor`** |
| **群組13優先順序，由左至右關聯性** |
| [邏輯 AND](../cpp/logical-and-operator-amp-amp.md) | [`&&`](../cpp/logical-and-operator-amp-amp.md) | **`and`** |
| **群組14優先順序，從左至右的關聯性** |
| [邏輯 OR](../cpp/logical-or-operator-pipe-pipe.md) | [`||`](../cpp/logical-or-operator-pipe-pipe.md) | **`or`** |
| **群組15優先順序，由右至左關聯性** |
| [條件式](../cpp/conditional-operator-q.md) | [`? :`](../cpp/conditional-operator-q.md) |
| **群組16優先順序，由右至左關聯性** |
| [指派](../cpp/assignment-operators.md) | [`=`](../cpp/assignment-operators.md) |
| [乘法指派](../cpp/assignment-operators.md) | [`*=`](../cpp/assignment-operators.md) |
| [除法指派](../cpp/assignment-operators.md) | [`/=`](../cpp/assignment-operators.md) |
| [模數指派](../cpp/assignment-operators.md) | [`%=`](../cpp/assignment-operators.md) |
| [加法指派](../cpp/assignment-operators.md) | [`+=`](../cpp/assignment-operators.md) |
| [減法指派](../cpp/assignment-operators.md) | [`-=`](../cpp/assignment-operators.md) |
| [左移指派](../cpp/assignment-operators.md) | [`<<=`](../cpp/assignment-operators.md) |
| [右移指派](../cpp/assignment-operators.md) | [`>>=`](../cpp/assignment-operators.md) |
| [位元 AND 指派](../cpp/assignment-operators.md) | [`&=`](../cpp/assignment-operators.md) | **`and_eq`** |
| [位元包含 OR 指派](../cpp/assignment-operators.md) | [`|=`](../cpp/assignment-operators.md) | **`or_eq`** |
| [位元互斥 OR 指派](../cpp/assignment-operators.md) | [`^=`](../cpp/assignment-operators.md) | **`xor_eq`** |
| **群組17優先順序，由右至左關聯性** |
| [擲回運算式](../cpp/try-throw-and-catch-statements-cpp.md) | [`throw`](../cpp/try-throw-and-catch-statements-cpp.md) |
| **群組18優先順序，從左至右的關聯性** |
| [千](../cpp/comma-operator.md) | [,](../cpp/comma-operator.md) |

## <a name="see-also"></a>另請參閱

[運算子多載](operator-overloading.md)
