---
title: frexp、 frexpf、 frexpl
ms.date: 04/05/2018
apiname:
- frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: c9e259f730d2d63d07032735be930f6f0fdb17e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563835"
---
# <a name="frexp-frexpf-frexpl"></a>frexp、 frexpf、 frexpl

取得浮點數的尾數和指數。

## <a name="syntax"></a>語法

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

*expptr*<br/>
預存整數指數的指標。

## <a name="return-value"></a>傳回值

**frexp**會傳回尾數。 如果*x*是 0，則此函數會傳回 0 則表示尾數和指數。 如果*expptr*是**NULL**，會叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL**且會傳回 0。

## <a name="remarks"></a>備註

**Frexp**函式會細分的浮點數值 (*x*) 分解為尾數 (*m*) 和指數 (*n*)，使得絕對值*m*大於或等於 0.5 並小於 1.0，以及*x* = *m* * 2<sup>*n*</sup>. 整數指數*n*所指向的位置會儲存*expptr*。

C + + 允許多載，因此您可以呼叫多載**frexp**。 在 C 程式中， **frexp**一律採用**double**並**int**指標並傳回**double**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**frexp**， **frexpf**， **frexpl**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
