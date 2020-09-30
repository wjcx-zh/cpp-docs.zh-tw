---
title: pow、powf、powl
description: Pow、powf 和 powl 的 API 參考;計算乘冪的。
ms.date: 08/31/2020
api_name:
- powl
- pow
- powf
- _o_pow
- _o_powf
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
ms.openlocfilehash: 8fb6679e2b509274b4ea60c410a81b54df866416
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505565"
---
# <a name="pow-powf-powl"></a>pow、powf、powl

計算以*y*乘冪的*x* 。

## <a name="syntax"></a>語法

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
define pow(X, Y) // Requires C11 or higher

double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>參數

*X*\
Base：

*Y*\
指數。

## <a name="return-value"></a>傳回值

傳回 *x*<sup>*y*</sup>的值。 溢位或反向溢位時不會列印錯誤訊息。

|x 和 y 的值|pow 的傳回值|
|-----------------------|-------------------------|
|*x* ！ = 0.0 且 *y* = = 0。0|1|
|*x* = = 0.0 且 *y* = = 0。0|1|
|*x* = = 0.0 和 *y* < 0|INF|

## <a name="remarks"></a>備註

**pow** 無法辨識大於 2<sup>64</sup> 的整數浮點值 (例如 1.0 e100) 。

**pow** 具有使用 Streaming SIMD Extensions 2 (SSE2) 的實作為。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

因為 c + + 允許多載，所以您可以呼叫 **pow**的各種多載。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函式，否則 **pow** 一律會採用兩個 **`double`** 值並傳回 **`double`** 值。

如果您使用 \<tgmath.h> `pow()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

`pow(int, int)` 已無法使用。 如果您使用此多載，編譯器可能會發出 [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md)。 若要避免這個問題，請將第一個參數轉換為 **`double`** 、 **`float`** 或 **`long double`** 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-|-|-|
|**pow**、 **powf**、 **powl**|\<math.h>|\<math.h> 或 \<cmath>|
|**pow** 宏 | \<tgmath.h> ||

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
