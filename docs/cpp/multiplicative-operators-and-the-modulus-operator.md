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
ms.openlocfilehash: 791f18793b49f7d3a986c3271fddef3acef33062
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367930"
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

- 乘法<strong>\*</strong>( )

- 司**/**( )

- 模數(從分部中分)**%**( )

這些二進位運算子具有由左至右的順序關聯性。

乘法類運算子接受算術類型的運算元。 模數運算符(**%**) 有更嚴格的要求,其操作數必須是積分類型。 (要取得浮點除法的其餘部分,請使用執行時函數[fmod](../c-runtime-library/reference/fmod-fmodf.md).)[標準轉換](standard-conversions.md)中介紹的轉換應用於操作數,結果是轉換類型。

乘法運算子會產生第一個運算元與第二個運算元相乘的結果。

除法運算子會產生第一個運算元除以第二個運算元的結果。

模數運算符產生以下表達式給出的剩餘部分,其中*e1*是第一個操作數 *,e2*是第二個操作數 *:e1* -*(e1* / *e2)* \* *e2,* 其中兩個操作數都是積分類型。

在除法或模數運算式中除以 0 並未定義，而且會產生執行階段錯誤。 因此，下列運算式會產生未定義的錯誤結果：

```cpp
i % 0
f / 0.0
```

如果乘法、除法或模數運算式的兩個運算元有相同的正負號，則結果為正數。 否則，結果為負數。 模數運算結果的正負號是由實作所定義。

> [!NOTE]
> 由於乘法類運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果乘法類運算的結果無法以轉換後的運算元類型表示，則資訊可能會遺失。

**Microsoft 特定的**

在 Microsoft C++ 中，模數運算式的結果一律與第一個運算元的正負號相同。

**結束微軟的**

如果兩個整數計算的除法不精確，而且只有一個運算元為負數，則結果會是小於除法運算會產生之實際值的最大整數 (範圍內，忽略正負號)。 例如,計算值 -11 / 3 是 -3.6666666666。 積分劃分的結果為 -3。

多乘運算符之間的關係由標識 *(e1* / *e2)* \* *e2* + *e2* % *e2* == *e1*給出。

## <a name="example"></a>範例

下列程式將示範乘法類運算子。 請注意,必須顯式強制轉換`10 / 3`到「**浮動**」類型,以避免截斷,以便兩個操作數在除法之前都是類型的**浮點**。

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
