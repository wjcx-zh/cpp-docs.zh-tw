---
title: 浮點數會失去精確度的原因
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298710"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>浮點數會失去精確度的原因

浮點十進位值通常不會有完全相同的二進位標記法。 這是 CPU 代表浮點數據之方式的副作用。 基於這個理由，您可能會遇到一些精確度遺失的情況，而某些浮點運算可能會產生非預期的結果。

此行為是下列其中一項的結果：

- 十進位數的二進位標記法可能不精確。

- 使用的數位之間的類型不符（例如，混用 float 和 double）。

為了解決此行為，大部分的程式設計人員都可以確保該值大於或小於所需的值，或取得並使用將會維持精確度的二進位編碼十進位（BCD）程式庫。

浮點值的二進位標記法會影響浮點計算的精確度和精確度。 Microsoft Visual C++ 使用[IEEE 浮點格式](ieee-floating-point-representation.md)。

## <a name="example"></a>範例

```c
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

針對 EPSILON，您可以使用常數 FLT_EPSILON （定義為 float 的 1.192092896 e-07F）或 DBL_EPSILON （定義為 double 做為 2.2204460492503131 e 016）。 您必須針對這些常數包含 float. h。 這些常數會定義為最小的正數位 x，因此 x + 1.0 不等於1.0。 因為這是非常小的數位，所以您應該針對涉及非常大數位的計算採用使用者定義的容錯。

## <a name="see-also"></a>請參閱

[最佳化程式碼](optimizing-your-code.md)
