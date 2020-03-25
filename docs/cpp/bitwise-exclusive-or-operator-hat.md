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
ms.openlocfilehash: 9a44dc60a985729aae79ed0e2e48c44adace647b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190712"
---
# <a name="bitwise-exclusive-or-operator-"></a>位元互斥 OR 運算子：^

## <a name="syntax"></a>語法

```
expression ^ expression
```

## <a name="remarks"></a>備註

位互斥 OR 運算子（ **^** ）會比較其第一個運算元的每個位與第二個運算元的對應位。 如果一個位元為 0 而另一個位元為 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。

位元互斥 OR 運算子的兩個運算元都必須為整數類資料類型。 [標準轉換](standard-conversions.md)中所涵蓋的一般算術轉換適用于運算元。

## <a name="operator-keyword-for-"></a>^ 的運算子關鍵字

**Xor**運算子是 **^** 的文字對等用法。 有兩種方式可存取您程式中的**xor**運算子：包含標頭檔 `iso646.h`，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能）編譯器選項進行編譯。

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
