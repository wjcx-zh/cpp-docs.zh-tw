---
title: 乘法類運算子和模數運算子
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
ms.openlocfilehash: 9a01672976703634c06724c9c655605bb433facf
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330381"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>乘法類運算子和模數運算子

## <a name="syntax"></a>語法

```
expression * expression
expression / expression
expression % expression
```

## <a name="remarks"></a>備註

乘法類運算子包括：

- 乘法 (<strong>\*</strong>)

- 除法 (**/**)

- 模數 （除法的餘數） (**%**)

這些二進位運算子具有由左至右的順序關聯性。

乘法類運算子接受算術類型的運算元。 模數運算子 (**%**) 具有較嚴格的要求，因為其運算元必須是整數類資料類型。 (若要取得浮點除法的餘數，請使用執行階段函式[fmod](../c-runtime-library/reference/fmod-fmodf.md)。)中涵蓋的轉換[標準轉換](standard-conversions.md)適用於運算元，結果是已轉換的型別。

乘法運算子會產生第一個運算元與第二個運算元相乘的結果。

除法運算子會產生第一個運算元除以第二個運算元的結果。

模數運算子會根據下列運算式會將剩餘所在*e1*是第一個運算元並*e2*是第二個： *e1* -(*e1* /  *e2*) \* *e2*，其中的兩個運算元都是整數類資料類型。

在除法或模數運算式中除以 0 並未定義，而且會產生執行階段錯誤。 因此，下列運算式會產生未定義的錯誤結果：

```cpp
i % 0
f / 0.0
```

如果乘法、除法或模數運算式的兩個運算元有相同的正負號，則結果為正數。 否則，結果為負數。 模數運算結果的正負號是由實作所定義。

> [!NOTE]
>  由於乘法類運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果乘法類運算的結果無法以轉換後的運算元類型表示，則資訊可能會遺失。

**Microsoft 專屬**

在 Microsoft C++ 中，模數運算式的結果一律與第一個運算元的正負號相同。

**結束 Microsoft 專屬**

如果兩個整數計算的除法不精確，而且只有一個運算元為負數，則結果會是小於除法運算會產生之實際值的最大整數 (範圍內，忽略正負號)。 例如，-11 的計算的值 / 3 為-3.666666666。 該整數除法的結果是-3。

乘法類運算子之間的關聯性根據身分識別 (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*。

## <a name="example"></a>範例

下列程式將示範乘法類運算子。 請注意的任一個運算元`10 / 3`必須明確地轉換為類型**浮點數**若要避免發生截斷，使兩個運算元的型別**float**除法之前。

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 乘法類運算子](../c-language/c-multiplicative-operators.md)