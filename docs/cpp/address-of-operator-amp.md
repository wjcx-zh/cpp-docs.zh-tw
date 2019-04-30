---
title: 傳址運算子： &amp;
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: a03a6100c372e059bd9ef2ddde0558da307923dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385020"
---
# <a name="address-of-operator-amp"></a>傳址運算子： &amp;

## <a name="syntax"></a>語法

```
& cast-expression
```

## <a name="remarks"></a>備註

一元傳址運算子 (**&**) 會採用其運算元的位址。 傳址運算子的運算元可以是函式指示項或左值，指定不是位元欄位的物件。

傳址運算子僅適用於基本、結構、類別或等位型別是在檔案範圍層級宣告的變數，或是註標的陣列參考。 在這些運算式中，未包含傳址運算子的常數運算式可以在傳址運算式中進行加法或減法運算。

套用至函式或左值時，運算式的結果會是衍生自運算元類型的指標類型 (右值)。 例如，如果運算元為類型**char**，運算式的結果屬於類型指標**char**。 傳址運算子套用至**const**或是**volatile**物件，會評估為`const type *`或`volatile type *`，其中**類型**是原始的型別物件。

當傳址運算子套用到限定名稱時，結果會取決於是否*限定名稱*指定靜態成員。 如果是，則結果為成員宣告中所指定類型的指標。 如果在成員不是靜態的結果是成員的指標*名稱*所表示的類別*限定類別名稱*。 (請參閱[主要運算式](../cpp/primary-expressions.md)如需詳細資訊*限定類別名稱*。)下列程式碼片段將示範成員是否為靜態的結果差異：

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

在這個範例中，因為 `&PTM::fValue` 是靜態成員，所以運算式 `float *` 會產生 `float PTM::*` 類型而不是 `fValue` 類型。

只有在清楚知道所參考的函式版本時，才會採用多載函式的位址。 請參閱[函式多載](function-overloading.md)濆爧髍孮特定位址的相關資訊的多載函式。

將傳址運算子套用至參考類型所產生的結果，與將運算子套用至參考繫結所在的物件產生的結果相同。 例如: 

## <a name="example"></a>範例

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Output

```Output
&d equals &rd
```

下列範例會使用傳址運算子將指標引數傳遞至函式：

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Output

```Output
25
```

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[左值參考宣告子：&](../cpp/lvalue-reference-declarator-amp.md)<br/>
[間接取值和傳址運算子](../c-language/indirection-and-address-of-operators.md)