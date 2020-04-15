---
title: remainder、remainderf、remainderl
ms.date: 4/2/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 4b70d3175a125d72ff67710c83899c44dbf72015
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332870"
---
# <a name="remainder-remainderf-remainderl"></a>remainder、remainderf、remainderl

計算兩個浮點值商數的餘數，四捨五入為最接近的整數值。

## <a name="syntax"></a>語法

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>參數

*X.*<br/>
分子。

*Y*<br/>
分母。

## <a name="return-value"></a>傳回值

*x* / y 的浮點餘*數。* 如果*y*的值為 0.0,**則餘數**將返回一個安靜的 NaN。 有關**printf**家族表示安靜 NaN 的資訊,請參閱[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**其餘**函數計算*浮* / 點餘數*r* x*y,* 以便*x* = *n* \* *y* + *r*,其中*n*是最接近*值 x* / *y*和*n*的整數,即使當 &#124; *n* - *x* / *y* &#124; = 1/2 時也是如此。 當*r* = 0 時 *,r*具有相同的符號*x*。

由於C++允許重載,因此可以調用獲取和返回**浮點**值或**長****雙精度**值的剩餘**項**的重載。 在 C 程式中,**其餘始終**採用兩**個雙**參數並傳回**一個雙**參數 。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------|-|
|**餘數**,**餘費**,**餘數**|\<math.h>|\<cmath> 或 \<math.h>|

如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
