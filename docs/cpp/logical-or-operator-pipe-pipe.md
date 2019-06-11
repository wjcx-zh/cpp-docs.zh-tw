---
title: '邏輯 OR 運算子: | |'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 5db1af870644d1552aeac813edce0985a31d95b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368678"
---
# <a name="logical-or-operator-"></a>邏輯 OR 運算子: | |

## <a name="syntax"></a>語法

> *logical-or-expression* **||** *logical-and-expression*

## <a name="remarks"></a>備註

使用邏輯 OR 運算子 ( **||** ) 會傳回布林值 TRUE，如果任一個或兩個運算元為 TRUE，否則傳回 FALSE。 運算元會隱含轉換成類型**bool**之前評估和結果為類型**bool**。 邏輯 OR 具有由左至右的順序關聯性。

邏輯 OR 運算子的運算元不需要屬於相同類型，不過必須屬於整數類資料類型或指標類型。 運算元通常是關聯或相等運算式。

第一個運算元會經過完整求值，並且會在所有副作用完成之後，才繼續求出邏輯 OR 運算式的值。

只有在第一個運算元的判斷值為 false (0) 時，才會計算第二個運算元的結果。 這樣在邏輯 OR 運算式為 true 時，就可以不必計算第二個運算元的結果。

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

在上述範例中，如果 `x` 等於 `w`、`y` 或 `z`，則 `printf` 函式的第二個引數判斷值為 true，並且印出值 1。 否則，它的判斷值為 false，並且印出值 0。 只要其中一項條件的判斷值為 true，求值就會停止。

## <a name="operator-keyword-for-124124"></a>運算子關鍵字&#124;&#124;

**或是**運算子是相等的文字 **||** 。 有兩種方式來存取 **或**在程式中的運算子： 包含標頭檔\<iso646.h> >，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。

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

[C++內建運算子優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 邏輯運算子](../c-language/c-logical-operators.md)