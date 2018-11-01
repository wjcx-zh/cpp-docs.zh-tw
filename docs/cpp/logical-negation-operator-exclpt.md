---
title: 邏輯負運算子：!
ms.date: 08/27/2018
f1_keywords:
- '!'
- Not
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 7b37e5108ca01d782c13508c0cd7a96b096cd745
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493715"
---
# <a name="logical-negation-operator-"></a>邏輯負運算子：!

## <a name="syntax"></a>語法

```
! cast-expression
```

## <a name="remarks"></a>備註

邏輯負運算子 (**！**) 會反轉其運算元的意義。 運算元必須是算術或指標類型 (或判斷值為算術或指標類型的運算式)。 運算元會隱含地轉換成類型**bool**。 如果轉換的運算元為 FALSE，結果為 TRUE如果轉換的運算元為 TRUE，則結果為 FALSE。 結果會是類型**bool**。

運算式*電子*，一元運算式`!e`相當於運算式`(e == 0)`，除了包含多載的運算子個。

## <a name="operator-keyword-for-"></a>! 的運算子關鍵字

**未**運算子是替代拼字 **！**。 有兩種方式來存取**未**在程式中的運算子： 包含標頭檔\<iso646.h> >，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。

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
