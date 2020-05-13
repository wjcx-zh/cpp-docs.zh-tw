---
title: 浮點數限制
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: ccd395eef319e57cecffad8a5278b6df1397f4cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373372"
---
# <a name="floating-limits"></a>浮點數限制

**Microsoft 特定的**

下表列出浮點常數值的限制。 這些限制也在標準頭檔\<float.h>中定义。

## <a name="limits-on-floating-point-constants"></a>浮點常數的限制

|持續性|意義|值|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|位數 q，使得有 q 個小數位數的浮點數可以捨入為浮點表示 (反向亦然)，而不會失去精確度。|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|最小正數 x，使得 x + 1.0 不會等於 1.0。|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|在浮點符號中指定的`FLT_RADIX`半徑中的位數。 半徑為 2;因此,這些值指定位。|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|最大可表示浮點數。|3.402823466e+38F<br/>1.7976931348623158e+308<br/>1.7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|最多整數,以便 10 個凸起到該數位是可表示的浮點數。|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|`FLT_RADIX`升到該數位的最大整數是可表示的浮點數。|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|最小正值。|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|最小負整數,以便 10 提升到該數位是可表示的浮點數。|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|升到該數位的`FLT_RADIX`最小負整數是可表示的浮點數。|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|指數表示的基數。|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|用於浮點添加的舍入模式。|1 (接近)<br/>1 (接近)<br/>1 (接近)|

> [!NOTE]
> 上表中的資訊在未來的產品版本中可能有所不同。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[整數限制](../cpp/integer-limits.md)
