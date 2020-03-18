---
title: 等號比較運算子：== 和 !=
ms.date: 11/04/2016
f1_keywords:
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: 7e42b66438579bc9be6274863366762b8b4ffbe9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444407"
---
# <a name="equality-operators--and-"></a>等號比較運算子：== 和 !=

## <a name="syntax"></a>語法

```
expression == expression
expression != expression
```

## <a name="remarks"></a>備註

二進位相等運算子會比較其運算元，以進行嚴格的相等或不等比較。

相等運算子等於 (`==`) 和不等於 (`!=`) 的優先順序低於關係運算子，但是它們的行為類似。 這些運算子的結果類型為**bool**。

如果兩個運算元具有相同的值，則等於運算子（`==`）會傳回**true** （1）;否則，它會傳回**false** （0）。 如果運算元的值不相同，則不等於運算子（`!=`）會傳回**true** ;否則，它會傳回**false**。

## <a name="operator-keyword-for-"></a>!= 的運算子關鍵字

`not_eq` 運算子是 `!=` 的文字對等用法。 有兩種方式可存取您程式中的 `not_eq` 運算子：包含標頭檔 `iso646.h`，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能）編譯器選項進行編譯。

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
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)