---
title: tgamma、tgammaf、tgammal
ms.date: 04/05/2018
apiname:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: c9ff92658163fc20ce21496aba34b22b3661748b
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518940"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal

判斷指定值的 gamma 函式。

## <a name="syntax"></a>語法

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
要尋找其 gamma 的值。

## <a name="return-value"></a>傳回值

如果成功，傳回的 gamma *x*。

如果，可能會發生範圍錯誤的變動*x*太大或太小的資料類型。 如果，則可能會發生網域錯誤或範圍錯誤*x* < = 0。

|問題|Return|
|-----------|------------|
|x = ±0|±INFINITY|
|x = 負整數|NaN|
|x =-INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|網域錯誤|NaN|
|極錯誤|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|
|溢位範圍錯誤|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|
|反向溢位範圍錯誤|正確的值 (四捨五入後)。|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，您可以呼叫多載**tgamma**採用並傳回**float**並**長** **double**類型。 在 C 程式中， **tgamma**一律採用並傳回**double**。

如果 x 為自然數，此函式會傳回 (x-1) 階乘。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**tgamma**， **tgammaf**， **tgammal**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
