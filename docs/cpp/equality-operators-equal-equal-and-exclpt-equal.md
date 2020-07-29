---
title: 等號比較運算子：== 和 !=
description: C + + 標準語言等於和不等於運算子語法，並使用。
ms.date: 07/23/2020
f1_keywords:
- '!='
- ==
- not_eq_cpp
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 567b83e99dce0354626f08a4788f1343314493b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227539"
---
# <a name="equality-operators--and-"></a>等號比較運算子：== 和 !=

## <a name="syntax"></a>語法

> *運算式* **`==`***運算式*\
> *運算式* **`!=`***運算式*

## <a name="remarks"></a>備註

二進位相等運算子會比較其運算元，以進行嚴格的相等或不等比較。

等號比較運算子（等於（ **`==`** ）和不等於（ **`!=`** ））的優先順序比關聯式運算子低，但其行為類似。 這些運算子的結果型別是 **`bool`** 。

**`==`** **`true`** 如果兩個運算元具有相同的值，則等於運算子（）會傳回，否則會傳回 **`false`** 。 **`!=`** **`true`** 如果運算元的值不相同，則不等於運算子（）會傳回，否則會傳回 **`false`** 。

## <a name="operator-keyword-for-"></a>！ = 的 Operator 關鍵字

C + + 會 **`not_eq`** 將指定為的替代拼寫 **`!=`** 。 （沒有的替代拼寫 **`==`** ）。在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="example"></a>範例

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

相等運算子可以比較相同類型成員的指標。 在這種比較中，會執行指標對成員的轉換。 成員指標也可以與判斷值為 0 的常數運算式進行比較。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C + + 內建運算子，優先順序;和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)
