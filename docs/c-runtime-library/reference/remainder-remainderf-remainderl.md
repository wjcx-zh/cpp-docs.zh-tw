---
title: remainder、remainderf、remainderl
description: 餘數、remainderf 和 remainderl 的 API 參考;這會計算兩個浮點值的商餘數，四捨五入為最接近的整數值。
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ef2b326bef2288b52dba8988749e030ff0b46077
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556005"
---
# <a name="remainder-remainderf-remainderl"></a>remainder、remainderf、remainderl

計算兩個浮點值商數的餘數，四捨五入為最接近的整數值。

## <a name="syntax"></a>語法

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
#define remainder(X, Y) // Requires C11 or higher

float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>參數

*X*\
分子。

*Y*\
分母。

## <a name="return-value"></a>傳回值

*X*  /  *y*的浮點餘數。 如果 *y* 的值為0.0， **餘數** 會傳回無訊息 NaN。 如需 **printf** 系列表示無訊息 NaN 的詳細資訊，請參閱 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**餘數**函式會計算*x*y 的浮點餘數*r*  /  *y* ，例如*x*  =  *n* \* *y*  +  *r*，其中*n*是最接近*x*  /  *y*值的整數，而*n*則是每次 &#124; *n*  -  *x*  /  *y* &#124; = 1/2 時。 當 *r* = 0 時， *r* 具有與 *x*相同的正負號。

因為 c + + 允許多載，所以您可以呼叫採用和傳回值之 **餘數** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **餘數** 一律會採用兩個 **`double`** 引數，並傳回 **`double`** 。

如果您使用 \<tgmath.h> `remainder()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------|-|
|**餘數**、 **remainderf**、 **remainderl**|\<math.h>|\<cmath> 或 \<math.h>|
|**餘數** 宏 | \<tgmath.h> ||

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

[浮點支援](../../c-runtime-library/floating-point-support.md)\
[ldiv、lldiv](ldiv-lldiv.md)\
[imaxdiv](imaxdiv.md)\
[fmod、fmodf](fmod-fmodf.md)\
[remquo、remquof、remquol](remquo-remquof-remquol.md)
