---
title: 邏輯負運算子：!
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446547"
---
# <a name="logical-negation-operator-"></a>邏輯負運算子：!

## <a name="syntax"></a>語法

```
! cast-expression
```

## <a name="remarks"></a>備註

邏輯負運算子（ **！** ）會反轉其運算元的意義。 運算元必須是算術或指標類型 (或判斷值為算術或指標類型的運算式)。 運算元會隱含地轉換成**bool**類型。 如果轉換的運算元為 FALSE，則結果為 TRUE;如果轉換的運算元為 TRUE，則結果為 FALSE。 結果的類型為**bool**。

若是運算式*e*，一元運算式 `!e` 等同于運算式 `(e == 0)`，除非牽涉到多載運算子。

## <a name="operator-keyword-for-"></a>! 的運算子關鍵字

**Not**運算子是 **！** 的替代拼寫。 有兩種方式可存取您程式中的**not**運算子：包含標頭檔 \<iso646 >，或使用[/za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能）編譯器選項進行編譯。

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
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算術運算子](../c-language/unary-arithmetic-operators.md)<br/>
