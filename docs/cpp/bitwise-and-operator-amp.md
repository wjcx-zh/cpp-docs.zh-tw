---
title: 位元 AND 運算子： &amp;
ms.date: 11/04/2016
f1_keywords:
- bitand
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b7d0d73802a5af7ab71e980d73eaff5c5b3c4bb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387704"
---
# <a name="bitwise-and-operator-amp"></a>位元 AND 運算子： &amp;

## <a name="syntax"></a>語法

```
expression & expression
```

## <a name="remarks"></a>備註

運算式可以是其他 and 運算式或 (受限於如下所述的限制) 相等的運算式、關聯運算式，加法運算式、乘法運算式、成員運算式的指標、cast 運算式、一元運算式、後置運算式或主要運算式。

位元的 AND 運算子 (**&**) 比較的第二個運算元的對應位元的第一個運算元的每個位元。 如果兩個位元皆為 1，則對應的結果位元會設為 1。 否則，對應結果位元會設為 0。

位元 AND 運算子的兩個運算元都必須為整數類型。 中涵蓋的一般算術轉換[標準轉換](standard-conversions.md)，適用於這些運算元。

## <a name="operator-keyword-for-"></a>運算子關鍵字 （& s)

**Bitand**運算子是相等的文字**&**。 有兩種方式來存取**bitand**在程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。

## <a name="example"></a>範例

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>另請參閱

[C++ 內建運算子、優先順序和順序關聯性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 位元運算子](../c-language/c-bitwise-operators.md)