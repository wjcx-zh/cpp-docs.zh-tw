---
title: 邏輯 AND 運算子：&amp;&amp;
description: C + + 標準語言邏輯 AND 運算子語法，並使用。
ms.date: 07/23/2020
f1_keywords:
- '&&'
- and_cpp
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: 431e76a2943c2373d6191f1fbe9f14c54cfaa6c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223690"
---
# <a name="logical-and-operator-ampamp"></a>邏輯 AND 運算子：&amp;&amp;

## <a name="syntax"></a>語法

> *運算式* **`&&`***運算式*

## <a name="remarks"></a>備註

**&&** **`true`** 如果兩個運算元都是，則邏輯 AND 運算子（）會傳回 **`true`** ，否則會傳回 **`false`** 。 在評估之前，運算元會隱含轉換成類型 **`bool`** ，而結果的類型為 **`bool`** 。 邏輯 AND 具有由左至右的順序關聯性。

邏輯 AND 運算子的運算元不需要具有相同的類型，但必須有布林值、整數或指標類型。 運算元通常是關聯或相等運算式。

第一個運算元會經過完整評估，而且所有副作用都會在邏輯 AND 運算式的評估繼續進行之前完成。

只有在第一個運算元評估為 **`true`** （非零）時，才會評估第二個運算元。 當邏輯 AND 運算式為時，此評估會排除第二個運算元的不必要評估 **`false`** 。 您可以使用這個最少運算評估來預防 null 指標取值，如下列範例所示：

```cpp
char *pch = 0;
// ...
(pch) && (*pch = 'a');
```

如果 `pch` 是 null (0)，則永遠不會評估運算式的右邊。 這種短路評估可讓您無法透過 null 指標進行指派。

## <a name="operator-keyword-for-"></a> && 的 Operator 關鍵字

C + + 會 **`and`** 將指定為的替代拼寫 **`&&`** 。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="example"></a>範例

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>另請參閱

[C + + 內建運算子、優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 邏輯運算子](../c-language/c-logical-operators.md)
