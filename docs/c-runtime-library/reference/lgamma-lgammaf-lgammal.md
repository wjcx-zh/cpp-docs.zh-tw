---
title: lgamma、lgammaf、lgammal
ms.date: 04/05/2018
apiname:
- lgamma
- lgammaf
- lgammal
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 43ce1599ab9161b9fadf5643ddd2ec739ab2d8b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533480"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma、lgammaf、lgammal

判斷指定值之 gamma 函式絕對值的自然對數。

## <a name="syntax"></a>語法

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
要計算的值。

## <a name="return-value"></a>傳回值

如果成功，傳回值的 gamma 函式絕對值的自然對數*x*。

|問題|Return|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ±0|+INFINITY|
|*x*= 非負值整數|+INFINITY|
|±INFINITY|+INFINITY|
|極錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|
|溢位範圍錯誤|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|

錯誤依 [_matherr](matherr.md) 中的指定回報。

## <a name="remarks"></a>備註

因為 c + + 允許多載，您可以呼叫多載**lgamma**採用並傳回**float**並**長** **double**類型。 在 C 程式中， **lgamma**一律採用並傳回**double**。

如果 x 為有理數，此函數會傳回的 (x-1) 階乘的對數。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**lgamma**， **lgammaf**， **lgammal**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[tgamma、tgammaf、tgammal](tgamma-tgammaf-tgammal.md)<br/>
