---
title: '位元包含 OR 運算子: |'
ms.date: 06/14/2018
f1_keywords:
- bitor
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 848bf3b2ec61084b59ab5b1ee6807f6066a4675e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184280"
---
# <a name="bitwise-inclusive-or-operator-"></a>位元包含 OR 運算子: |

## <a name="syntax"></a>語法

> *expression1* **|** *expression2*

## <a name="remarks"></a>備註

位元包含 OR 運算子 (**&#124;**) 會比較其第二個運算元的對應位元的第一個運算元的每個位元。 如果任一位元為 1，則對應結果位元會設為 1。 否則，對應結果位元會設為 0。

位元包含 OR 運算子的兩個運算元都必須為整數類資料類型。 中涵蓋的一般算術轉換[標準轉換](standard-conversions.md)適用於這些運算元。

## <a name="operator-keyword-for-124"></a>運算子關鍵字&#124;

**Bitor**運算子是相等的文字 **&#124;**。 有兩種方式來存取**bitor**在程式中的運算子： 包含標頭檔\<iso646.h> >，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。

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