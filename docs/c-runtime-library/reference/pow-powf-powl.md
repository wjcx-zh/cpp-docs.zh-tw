---
title: pow、powf、powl
ms.date: 04/05/2018
api_name:
- powl
- pow
- powf
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 863d2b76ec131670b10eefc086fa3485bd0a983d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950293"
---
# <a name="pow-powf-powl"></a>pow、powf、powl

計算*x*到*y*的乘冪。

## <a name="syntax"></a>語法

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
底數。

*y*<br/>
指數。

## <a name="return-value"></a>傳回值

傳回*x*<sup>*y*</sup>的值。 溢位或反向溢位時不會列印錯誤訊息。

|x 和 y 的值|pow 的傳回值|
|-----------------------|-------------------------|
|*x* ！ = 0.0 和*y* = = 0。0|1|
|*x* = = 0.0 和*y* = = 0。0|1|
|*x* = = 0.0 和*y* < 0|INF|

## <a name="remarks"></a>備註

**pow**無法辨識大於 2<sup>64</sup>的整數浮點值（例如，1.0 e100）。

**pow**具有使用 Streaming SIMD Extensions 2 （SSE2）的執行。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

因為C++允許多載，所以您可以呼叫**pow**的任何不同多載。 在 C 程式中， **pow**一律會採用兩個**雙精度浮點數**，並傳回**雙精度**值。

`pow(int, int)` 已無法使用。 如果您使用這個多載，編譯器可能會發出[C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md)。 若要避免這個問題，請將第一個參數轉換為**double**、 **float**或**long** **double**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-|-|-|
|**pow**、 **powf**、 **powl**|\<math.h>|\<math.h> 或 \<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md) <br/>
[exp、expf、expl](exp-expf.md) <br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md) <br/>
[sqrt、sqrtf、sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
