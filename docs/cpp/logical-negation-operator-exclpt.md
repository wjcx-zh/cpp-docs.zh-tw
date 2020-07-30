---
title: 邏輯否定運算子：!
description: C + + 標準語言邏輯否定運算子語法和使用。
ms.date: 07/23/2020
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: fdd2e7a71b791375f898372d058a5eeb2afc59f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223677"
---
# <a name="logical-negation-operator-"></a>邏輯否定運算子：!

## <a name="syntax"></a>語法

> **`!`***cast-運算式*

## <a name="remarks"></a>備註

邏輯負運算子（ **`!`** ）會反轉其運算元的意義。 運算元必須是算術或指標類型 (或判斷值為算術或指標類型的運算式)。 運算元會隱含地轉換成類型 **`bool`** 。 **`true`** 如果轉換的運算元為，則結果為 **`false`** ; **`false`** 如果轉換的運算元為，則結果為 **`true`** 。 結果的類型為 **`bool`** 。

若為運算式 `e` ，一元運算式 `!e` 就相當於運算式 `(e == 0)` ，但牽涉到多載運算子的情況除外。

## <a name="operator-keyword-for-"></a>！的 Operator 關鍵字

C + + 會 **`not`** 將指定為的替代拼寫 **`!`** 。 在 C 中，替代的拼寫是以宏的形式在 \<iso646.h> 標頭中提供。 在 c + + 中，替代的拼寫是關鍵字;使用 \<iso646.h> 或 c + + 對等用法 \<ciso646> 已被取代。 在 Microsoft c + + 中， [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) 需要或編譯器選項才能啟用替代的拼寫。

## <a name="example"></a>範例

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[C + + 內建運算子、優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算術運算子](../c-language/unary-arithmetic-operators.md)<br/>
