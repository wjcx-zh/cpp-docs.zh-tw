---
title: Math 常數
ms.date: 11/04/2016
f1_keywords:
- c.constants
helpviewer_keywords:
- M_PI constant
- M_PI_2 constant
- math constants
- M_2_PI constant
- M_1_PI constant
- M_E constant
- USE_MATH_DEFINES constant
- M_LOG2E constant
- M_LOG10E constant
- M_LN10 constant
- M_SQRT1_2 constant
- _USE_MATH_DEFINES constant
- M_PI_4 constant
- constants, math
- M_2_SQRTPI constant
- M_SQRT2 constant
- M_LN2 constant
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
ms.openlocfilehash: bd17004585e0238f36b939b19379ef62e349fac9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744161"
---
# <a name="math-constants"></a>Math 常數

## <a name="syntax"></a>語法

```
#define _USE_MATH_DEFINES // for C++
#include <cmath>

#define _USE_MATH_DEFINES // for C
#include <math.h>
```

## <a name="remarks"></a>備註

下列符號是針對其所表示之運算式的值進行定義：

|符號|運算式|值|
|------------|----------------|-----------|
|M_E|e|2.71828182845904523536|
|M_LOG2E|log2(e)|1.44269504088896340736|
|M_LOG10E|log10(e)|0.434294481903251827651|
|M_LN2|ln(2)|0.693147180559945309417|
|M_LN10|ln(10)|2.30258509299404568402|
|M_PI|pi|3.14159265358979323846|
|M_PI_2|pi/2|1.57079632679489661923|
|M_PI_4|pi/4|0.785398163397448309616|
|M_1_PI|1/pi|0.318309886183790671538|
|M_2_PI|2/pi|0.636619772367581343076|
|M_2_SQRTPI|2/sqrt(pi)|1.12837916709551257390|
|M_SQRT2|sqrt(2)|1.41421356237309504880|
|M_SQRT1_2|1/sqrt(2)|0.707106781186547524401|

標準 C/C++ 中沒有定義數學常數。 若要使用它們，您必須先定義 `_USE_MATH_DEFINES`，然後包含 cmath 或 math.h。

當您的專案是以發行模式建置時，ATLComTime.h 檔案會包含 math.h。 如果您在同時包含 ATLComTime.h 的專案中使用一或多個數學常數，則必須在包含 ATLComTime.h 之前定義 `_USE_MATH_DEFINES`。

## <a name="see-also"></a>另請參閱

[全域常數](../c-runtime-library/global-constants.md)
