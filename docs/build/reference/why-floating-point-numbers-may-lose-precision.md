---
title: 浮點數會失去精確度的原因 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de54610676ade49f7ce41e00ed0049b20e46709c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700009"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>浮點數會失去精確度的原因

浮點數十進位值通常不需要精確的二進位表示法。 這是 CPU 的浮點數資料的表示方式的副作用。 基於這個理由，您可能會遇到一些遺失有效位數的情況下，，而且某些浮點運算可能會產生非預期的結果。

此行為是下列其中一項的結果：

- 可能不精確的十進位數字的二進位表示法。

- 所使用的號碼 （例如，混用 float 和 double） 之間沒有不相符的類型。

若要解決這個問題，請確定值大於或小於功能所需的大多數程式設計師，或它們取得，並使用會維持有效位數的二進碼十進位 (BCD) 程式庫中。

有效位數和精確度的浮點數計算，會影響浮點值的二進位表示法。 使用 Microsoft Visual c + + [IEEE 浮點數格式](../../build/reference/ieee-floating-point-representation.md)。

## <a name="example"></a>範例

```
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>註解

EPSILON、 您可以使用常數 FLT_EPSILON，定義為 1.192092896e 浮點數的-07F，或 DBL_EPSILON，定義為雙精度浮點數為 2.2204460492503131e-016。 您需要包含這些常數的 float.h。 這些常數會定義為最小正數 x 數字，例如 x + 1.0 不等於 1.0。 因為這是很小的數目時，您應該採用使用者定義的功能，包含非常大量的計算。

## <a name="see-also"></a>另請參閱

[最佳化程式碼](../../build/reference/optimizing-your-code.md)