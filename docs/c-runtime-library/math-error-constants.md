---
title: 運算錯誤常數
ms.date: 11/04/2016
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
ms.openlocfilehash: f51d9a3a28118d922f81a44e31c9abc610645f13
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524985"
---
# <a name="math-error-constants"></a>運算錯誤常數

## <a name="syntax"></a>語法

```

#include <math.h>
```

## <a name="remarks"></a>備註

執行階段程式庫的數學常式可能會產生數學錯誤常數。

這些錯誤 (如下所述) 會對應至在 MATH.H 中定義的例外狀況類型，並會在發生數學錯誤時由 `_matherr` 函式傳回。

|常數|意義|
|--------------|-------------|
|`_DOMAIN`|函式的引數位於函式的定義域之外。|
|`_OVERFLOW`|結果太大而無法以函式的傳回類型表示。|
|`_PLOSS`|發生精確度部分遺失。|
|`_SING`|引數獨特性：函式的引數具有不合法的值。 (例如，值 0 傳遞至要求非零值的函式)。|
|`_TLOSS`|發生精確度完全遺失。|
|`_UNDERFLOW`|結果太小而無法表示。|

## <a name="see-also"></a>請參閱

[_matherr](../c-runtime-library/reference/matherr.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)