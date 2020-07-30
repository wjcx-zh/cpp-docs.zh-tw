---
title: 一補數運算子：~
description: C + + 標準語言一補數運算子語法，並使用。
ms.date: 07/23/2020
f1_keywords:
- "~"
- compl_cpp
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 89c67855cd67df2af315cea941b487e7462889b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227240"
---
# <a name="ones-complement-operator-"></a>一補數運算子：~

## <a name="syntax"></a>語法

```cpp
~ cast-expression
```

## <a name="remarks"></a>備註

一補數運算子（ **`~`** ），有時稱為*位補數*運算子，會產生其運算元的位一補數。 也就是說，運算元中是 1 的每個位元，在結果中都是 0。 反之，運算元中是 0 的每個位元，在結果中都是 1。 一補數運算子的運算元必須是整數類資料類型。

## <a name="operator-keyword-for-"></a>~ 的 Operator 關鍵字

C + + 會 **`compl`** 將指定為的替代拼寫 **`~`** 。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="example"></a>範例

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

在這個範例中，指派至 `y` 的新值是不帶正負號的值 0xFFFF 或 0x0000 的 1 補數。

整數提升會在整數運算元上執行。 運算元升級為的類型是結果類型。 如需整數提升的詳細資訊，請參閱[標準轉換](standard-conversions.md)。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](expressions-with-unary-operators.md)<br/>
[C + + 內建運算子、優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算術運算子](../c-language/unary-arithmetic-operators.md)
