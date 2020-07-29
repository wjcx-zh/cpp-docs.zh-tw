---
title: 位 AND 運算子：&amp;
description: C + + 標準語言位 AND 運算子語法，並使用。
ms.date: 07/23/2020
f1_keywords:
- bitand_cpp
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: 7e78e4003a31ee59ebd974275df784b7a76e73ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229112"
---
# <a name="bitwise-and-operator-amp"></a>位 AND 運算子：&amp;

## <a name="syntax"></a>語法

> *運算式* **`&`***運算式*

## <a name="remarks"></a>備註

位 AND 運算子（ **`&`** ）會比較第一個運算元的每個位與第二個運算元的對應位。 如果這兩個位元都是 1，則對應的結果位元會設為 1。 否則，對應的結果位元會設為 0。

位 AND 運算子的兩個運算元都必須有整數類資料類型。 [標準轉換](standard-conversions.md)中所涵蓋的一般算術轉換適用于運算元。

## <a name="operator-keyword-for-"></a>& 的 Operator 關鍵字

C + + 會 **`bitand`** 將指定為的替代拼寫 **`&`** 。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

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

[C + + 內建運算子、優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 位元運算子](../c-language/c-bitwise-operators.md)
