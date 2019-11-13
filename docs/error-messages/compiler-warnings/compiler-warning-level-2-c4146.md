---
title: 編譯器警告（層級2） C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: d595befc80d954c8fb84f83ad6c4e0cb5f4fcf26
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052160"
---
# <a name="compiler-warning-level-2-c4146"></a>編譯器警告（層級2） C4146

一元減號運算子套用至不帶正負號的類型，結果仍為未簽署

不帶正負號的類型只能保存非負數值，因此在套用至不帶正負號的類型時，一元減號（否定）通常不合理。 運算元和結果都不是負數。

實際上，當程式設計人員嘗試表示最小整數值時（也就是-2147483648），就會發生這種情況。 這個值無法寫入為-2147483648，因為運算式會以兩個階段進行處理：

1. 數位2147483648已評估。 因為它大於最大整數值2147483647，所以2147483648的類型不是[int](../../c-language/integer-types.md)，但 `unsigned int`。

1. 一元減號會套用至值，而不帶正負號的結果也會是2147483648。

不帶正負號的結果類型可能會導致非預期的行為。 如果在比較中使用結果，則可能會使用不帶正負號的比較，例如，當另一個運算元是 `int`時。 這會說明為什麼下面的範例程式只會列印一行。

不會列印預期的第二行 `1 is greater than the most negative int`，因為 `((unsigned int)1) > 2147483648` 為 false。

您可以 INT_MIN 使用 C4146，其類型為**帶正負**號的 INT，藉以避免。

## <a name="example"></a>範例

下列範例會產生 C4146：

```cpp
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