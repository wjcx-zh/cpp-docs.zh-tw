---
title: 關係運算子： &lt;、&gt;、&lt;= 和 &gt;=
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 38e05b78d334ca690d9523797f7ca1813834c5d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179116"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>關係運算子： &lt;、&gt;、&lt;= 和 &gt;=

## <a name="syntax"></a>語法

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>備註

二元關係運算子決定下列關聯性：

- 小於（ **\<** ）

- 大於（ **>** ）

- 小於或等於（ **\<=** ）

- 大於或等於（ **>=** ）

關係運算子具有由左到右的順序關聯性。 關係運算子的兩個運算元都必須是算術或指標類型。 它們會產生**bool**類型的值。 如果運算式中的關聯性是 false，傳回的值會是**false** （0）;否則，傳回的值為**true** （1）。

## <a name="example"></a>範例

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

上述範例中的運算式必須以括弧括住，因為資料流程插入運算子（ **<<** ）的優先順序高於關係運算子。 因此，不加括弧的第一個運算式會評估為：

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

[標準轉換](standard-conversions.md)中所涵蓋的一般算術轉換適用于算術類型的運算元。

## <a name="comparing-pointers"></a>比較指標

比較相同類型的兩個物件指標時，結果是取決於程式的位址空間中所指向的物件位置。 指標也可以與評估為0的常數運算式或 `void *`的類型指標進行比較。 如果對 `void *`類型的指標進行指標比較，則會將另一個指標隱含地轉換成類型 `void *`。 然後才進行比較。

兩個不同類型的指標無法進行比較，除非：

- 其中一個類型是衍生自另一個類型的類別類型。

- 至少有一個指標明確轉換（cast）為類型 `void *`。 （另一個指標會隱含地轉換成類型 `void *` 以進行轉換）。

相同類型且指向相同物件之兩個指標的比較結果一定為相等。 如果將物件的兩個非靜態成員指標相互比較，則適用下列規則：

- 如果類別類型不是聯**集**，而且如果兩個成員不是以*存取規範*（例如**public**、 **protected**或**private**）分隔，則最後宣告之成員的指標將會比稍早宣告的成員指標還要大。

- 如果兩個成員以*存取規範*分隔，則結果會是未定義的。

- 如果類別類型為聯**集**，則該等位中不同資料成員的指標**會比較相等**。

如果兩個指標指向相同陣列的元素，或指向超出陣列結尾的元素一，則具有較高註標的物件指標比較結果會較高。 只有在指標參考相同陣列中的物件或超出陣列結尾的位置一時，才能保證指標比較有效。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 關係和等號比較運算子](../c-language/c-relational-and-equality-operators.md)
