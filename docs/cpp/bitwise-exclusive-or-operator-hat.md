---
title: 位元互斥 OR 運算子：^
description: C + + 標準語言專屬 OR 運算子語法和用法。
ms.date: 09/21/2020
f1_keywords:
- xor_cpp
- ^
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 4823c245ffca7032347e37c0c25c2963407733a7
ms.sourcegitcommit: f656092eebbcb148ca4d3b7a6a8508eff8f7e85f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2020
ms.locfileid: "90836624"
---
# <a name="bitwise-exclusive-or-operator-"></a>位元互斥 OR 運算子：^

## <a name="syntax"></a>語法

> *運算式* **`^`***運算式*

## <a name="remarks"></a>備註

位互斥 OR 運算子 () 會將 **`^`** 其第一個運算元的每個位與第二個運算元的對應位進行比較。 如果其中一個運算元的位為0，而另一個運算元中的位為1，則對應的結果位會設為1。 否則，對應的結果位元會設為 0。

運算子的兩個運算元都必須有整數類資料類型。 [標準轉換](standard-conversions.md)中涵蓋的一般算術轉換適用于運算元。

如需 **`^`** c + +/cli 和 c + +/cx 中字元替代用法的詳細資訊，請參閱 [ (^)  (c + +/Cli 和 c + +/cx) 的物件運算子控制碼 ](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)。

## <a name="operator-keyword-for-"></a>^ 的 Operator 關鍵字

C + + **`xor`** 將指定為的替代拼寫 **`^`** 。 在 C 中，會在標頭中以宏的形式提供替代的拼寫 \<iso646.h> 。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等專案 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

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

[C + + 內建運算子、優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
