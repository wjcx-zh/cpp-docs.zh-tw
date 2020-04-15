---
title: pow、powf、powl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b181959ac05814a673ab11f33e4cfc5a39e3869e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333110"
---
# <a name="pow-powf-powl"></a>pow、powf、powl

*計算*x 提升到*y*的功率。

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

*X.*<br/>
Base：

*Y*<br/>
指數。

## <a name="return-value"></a>傳回值

傳回*x* <sup>*xy*</sup>的值 。 溢位或反向溢位時不會列印錯誤訊息。

|x 和 y 的值|pow 的傳回值|
|-----------------------|-------------------------|
|*x* != 0.0 和*y* = 0.0|1|
|*x* = 0.0 和*y* = 0.0|1|
|*x* = 0.0 和*y* < 0|INF|

## <a name="remarks"></a>備註

**pow**無法識別大於 2<sup>64(</sup>例如,1.0E100)的積分浮點值。

**pow**具有使用流式 SIMD 擴展 2 (SSE2) 的實現。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

由於C++允許重載,您可以調用**pow**的任何各種過載。 在 C 程式中 **,pow**始終採用兩**個雙精度**值並返回**一個雙**值。

`pow(int, int)` 已無法使用。 如果使用此重載,編譯器可能會發出[C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md)。 為了避免此問題,將第一個參數轉換為**雙精度**、**浮動**或**長****雙**精度。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-|-|-|
|**波夫**,**波夫**,**家禽**|\<math.h>|\<math.h> 或 \<cmath>|

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
