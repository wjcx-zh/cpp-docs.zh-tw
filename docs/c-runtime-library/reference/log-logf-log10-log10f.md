---
title: log、logf、logl、log10、log10f、log10l
description: Log、logf、記錄、log10、log10f 和 log10l 的 API 參考;計算對數的。
ms.date: 9/1/2020
api_name:
- log10f
- logf
- log10
- log
- log10l
- logl
- _o_log
- _o_log10
- _o_log10f
- _o_logf
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
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- log10l function
- logl function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
ms.openlocfilehash: f308281705170308ec83e4a5efd9c7825ba47591
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556278"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>log、logf、logl、log10、log10f、log10l

計算對數。

## <a name="syntax"></a>語法

```C
double log(double x);
float logf(float x);
long double logl(double x);
double log10(double x);
float log10f (float x);
long double log10l(double x);
#define log(X) // Requires C11 or higher
#define log10(X) // Requires C11 or higher

float log(float x);  // C++ only
long double log(long double x);  // C++ only
float log10(float x);  // C++ only
long double log10(long double x);  // C++ only
```

### <a name="parameters"></a>參數

*X*\
要求得其對數的值。

## <a name="return-value"></a>傳回值

如果成功，則 **記錄** 函式會傳回 x 的自然對數 (底數 *e*) *x* 。 **Log10**函數會傳回以10為底數的對數。 如果 *x* 是負數，則根據預設，這些函式會傳回不定的 (IND) 。 如果 *x* 為0，則會傳回無限大 (INF) 。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± QNAN、IND|無|_DOMAIN|
|±0|ZERODIVIDE|_SING|
|*x* < 0|無效|_DOMAIN|

**記錄** 和 **log10** 具有使用 Streaming SIMD Extensions 2 (SSE2) 的實作為。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

## <a name="remarks"></a>備註

C + + 允許多載，所以您可以呼叫採用和傳回值之 **記錄** 檔和 **log10** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **log** 和 **log10** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `log()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**log**、 **logf**、 **記錄**、 **log10**、 **log10f**、 **log10l**|\<math.h>|
|**記錄** 宏 | \<tgmath.h> |

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_log.c
/* This program uses log and log10
* to calculate the natural logarithm and
* the base-10 logarithm of 9,000.
*/

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 9000.0;
   double y;

   y = log( x );
   printf( "log( %.2f ) = %f\n", x, y );
   y = log10( x );
   printf( "log10( %.2f ) = %f\n", x, y );
}
```

```Output
log( 9000.00 ) = 9.104980
log10( 9000.00 ) = 3.954243
```

若要產生其他底數的對數，請使用數學關聯︰a 的對數底數 b == 自然對數 (a) / 自然對數 (b)。

```cpp
// logbase.cpp
#include <math.h>
#include <stdio.h>

double logbase(double a, double base)
{
   return log(a) / log(base);
}

int main()
{
   double x = 65536;
   double result;

   result = logbase(x, 2);
   printf("Log base 2 of %lf is %lf\n", x, result);
}
```

```Output
Log base 2 of 65536.000000 is 16.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md) <br/>
[exp、expf、expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow、powf、powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
