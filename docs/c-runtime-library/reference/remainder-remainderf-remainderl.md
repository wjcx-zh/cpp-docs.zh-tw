---
title: remainder、remainderf、remainderl
ms.date: 04/05/2018
apiname:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 9a9abe82e69122ca87f44e293e1da725c97045d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572740"
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

*x*<br/>
分子。

*y*<br/>
分母。

## <a name="return-value"></a>傳回值

浮點餘數*x* / *y*。 如果值*y*是 0.0，**餘數**傳回無訊息 NaN。 如需無訊息 NaN 的表示法**printf**系列，請參閱[printf、 _printf_l、 wprintf、 _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**餘數**函式會計算浮點餘數*r*的*x* / *y*使得*x*  =  *n* \* *y* + *r*，其中*n*是值最接近的整數*x* / *y*並*n*甚至是每當&#124; *n*  - *x* / *y* &#124; = 1/2。 當*r* = 0， *r*具有相同的簽章為*x*。

因為 c + + 允許多載，您可以呼叫多載**餘數**採用並傳回**float**或**長** **double**值。 在 C 程式中，**餘數**一律會採用兩個**double**引數並傳回**double**。

## <a name="requirements"></a>需求

|功能|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------|-|
|**餘數**， **remainderf**， **remainderl**|\<math.h>|\<cmath> 或 \<math.h>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
