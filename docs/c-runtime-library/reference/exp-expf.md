---
title: exp、expf、expl
ms.date: 04/05/2018
api_name:
- expf
- expl
- exp
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
ms.openlocfilehash: 380f3e861b3ae1ba2f57aa781c32829771612b9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941629"
---
# <a name="exp-expf-expl"></a>exp、expf、expl

計算指數。

## <a name="syntax"></a>語法

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
用來 exponentiate 自然對數底數*e*的浮點值。

## <a name="return-value"></a>傳回值

**Exp**函數會傳回浮點參數*x*的指數值（如果成功）。 也就是說，結果是*e*<sup>*x*</sup>，其中*e*是自然對數的基底。 在溢位時，函數會傳回 INF （無限大），而在下溢時， **exp**會傳回0。

|Input|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± Quiet NaN，不定|None|_DOMAIN|
|±無限大|INVALID|_DOMAIN|
|x ≥ 7.097827e+002|INEXACT+OVERFLOW|OVERFLOW|
|X ≤ -7.083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|

**Exp**函數具有使用 Streaming SIMD Extensions 2 （SSE2）的執行。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

## <a name="remarks"></a>備註

C++允許多載，因此您可以呼叫採用**float**或**long double**引數之**exp**的多載。 在 C 程式中， **exp**一律會採用並傳回**雙精度浮點數**。

## <a name="requirements"></a>需求

|函數|必要的 C 標頭|必要的 C++ 標頭|
|--------------|---------------------|---|
|**exp**、 **expf**、**總管**|\<math.h>|\<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
