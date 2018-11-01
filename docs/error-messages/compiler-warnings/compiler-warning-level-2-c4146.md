---
title: 編譯器警告 （層級 2） C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: 8b3090f1bc3a64752ede4dab2b1e1b5cd800057d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555566"
---
# <a name="compiler-warning-level-2-c4146"></a>編譯器警告 （層級 2） C4146

一元減號運算子套用至不帶正負號的類型，所得的結果不帶正負號

不帶正負號的類型可以保留只有非負數的值，因此一元減號 （負） 通常是毫無意義時套用至不帶正負號的型別。 運算元和結果都是非負數。

實際上，發生這種情況時，程式設計人員正嘗試 express 的最小整數值，這是介於-2147483648。 無法為-2147483648 寫入此值，因為運算式會處理兩個階段：

1. 評估數字 2147483648 時。 2147483648 類型是大於 2147483647 的最大整數值，因為不是[int](../../c-language/integer-types.md)，但`unsigned int`。

1. 一元減號會套用至不帶正負號的結果，這也剛好是 2147483648 值。

結果的不帶正負號的型別可能會導致非預期的行為。 如果相較之下，使用該結果，則不帶正負號的比較可能使用，例如，當另一個運算元是`int`。 本節將說明為什麼下面的範例程式只會列印一行。

預期的第二行中， `1 is greater than the most negative int`，不會因為列印`((unsigned int)1) > 2147483648`為 false。

您可以使用 INT_MIN limits.h，具有類型，以避免 C4146**帶正負號 int**。

## <a name="example"></a>範例

下列範例會產生 C4146:

```
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```