---
title: 邏輯 OR 運算子：  &#124;&#124;
description: C + + 標準語言邏輯 OR 運算子語法，並使用。
ms.date: 07/23/2020
f1_keywords:
- '||'
- or_cpp
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 1845aef59f88d5dd044cefedd21cb618e1102e13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225991"
---
# <a name="logical-or-operator-124124"></a>邏輯 OR 運算子：  &#124;&#124;

## <a name="syntax"></a>語法

> *邏輯 or 運算式* **`||`***邏輯 and 運算式*

## <a name="remarks"></a>備註

**`||`** **`true`** 如果任一個或兩個運算元都是，則邏輯 OR 運算子（）會傳回布林值 **`true`** ，否則會傳回 **`false`** 。 在評估之前，運算元會隱含轉換成類型 **`bool`** ，而結果的類型為 **`bool`** 。 邏輯 OR 具有由左至右的順序關聯性。

邏輯 OR 運算子的運算元不一定要有相同的類型，但它們必須是布林值、整數或指標類型。 運算元通常是關聯或相等運算式。

第一個運算元會經過完整求值，並且會在所有副作用完成之後，才繼續求出邏輯 OR 運算式的值。

只有在第一個運算元評估為時，才會評估第二個運算元 **`false`** ，因為當邏輯 OR 運算式為時，不需要進行評估 **`true`** 。 這就是所謂的*短路*評估。

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

在上述範例中，如果 `x` 等於 `w` 、或，則函式 `y` `z` 的第二個引數會 `printf` 評估為 **`true`** ，然後將它升級為整數，並列印值1。 否則，它會評估為 **`false`** ，並列印值0。 一旦其中一個條件評估為，就會 **`true`** 停止評估。

## <a name="operator-keyword-for-124124"></a> &#124;&#124; 的 Operator 關鍵字

C + + 會 **`or`** 將指定為的替代拼寫 **`||`** 。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="example"></a>範例

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>另請參閱

[C + + 內建運算子、優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 邏輯運算子](../c-language/c-logical-operators.md)
