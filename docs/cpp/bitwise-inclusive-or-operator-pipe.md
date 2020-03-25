---
title: 位元非互斥 OR 運算子：|
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 38def2b1ac585c751699227d2a065b45145d290d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190751"
---
# <a name="bitwise-inclusive-or-operator-"></a>位元非互斥 OR 運算子：|

## <a name="syntax"></a>語法

> *運算式*2 **|** *運算式*2

## <a name="remarks"></a>備註

位包含 OR 運算子（ **&#124;** ）會比較其第一個運算元的每個位與第二個運算元的對應位。 如果其中一個位元是 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。

位元包含 OR 運算子的兩個運算元都必須為整數類資料類型。 [標準轉換](standard-conversions.md)中所涵蓋的一般算術轉換適用于運算元。

## <a name="operator-keyword-for-124"></a>的 Operator 關鍵字&#124;

**Bitor**運算子是的文字對等用法 **&#124;** 。 有兩種方式可存取您程式中的**bitor**運算子：包含標頭檔 \<iso646 >，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能）編譯器選項進行編譯。

## <a name="example"></a>範例

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>另請參閱

[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 位元運算子](../c-language/c-bitwise-operators.md)
