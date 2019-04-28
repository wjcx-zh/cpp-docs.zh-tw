---
title: 位元互斥 OR 運算子：^
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 07af1b507cf256b84ac2f0f2db4061790a23555a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232010"
---
# <a name="bitwise-exclusive-or-operator-"></a>位元互斥 OR 運算子：^

## <a name="syntax"></a>語法

```
expression ^ expression
```

## <a name="remarks"></a>備註

使用位元排除 OR 運算子 (**^**) 會比較其第二個運算元的對應位元的第一個運算元的每個位元。 如果其中一個位元為 0，而另一個位元為 1，則會將對應的結果位元設為 1。 否則，對應結果位元會設為 0。

位元互斥 OR 運算子的兩個運算元都必須為整數類資料類型。 中涵蓋的一般算術轉換[標準轉換](standard-conversions.md)適用於這些運算元。

## <a name="operator-keyword-for-"></a>^ 的運算子關鍵字

**Xor**運算子是相等的文字**^**。 有兩種方式來存取**xor**在程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。

## <a name="example"></a>範例

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>另請參閱

[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)