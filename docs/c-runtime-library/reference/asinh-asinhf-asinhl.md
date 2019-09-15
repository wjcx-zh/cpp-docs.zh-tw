---
title: asinh、asinhf、asinhl
ms.date: 04/05/2018
api_name:
- asinh
- asinhf
- asinhl
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
- asinhf
- asinhl
- asinh
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
ms.openlocfilehash: f4d93f121c0124293a5bdff9041d0adfaab5d83c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939646"
---
# <a name="asinh-asinhf-asinhl"></a>asinh、asinhf、asinhl

計算反雙曲正弦。

## <a name="syntax"></a>語法

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**Asinh**函數會傳回*x*的反雙曲正弦（arc 雙曲正弦）。 此函式在浮點網域中有效。 如果*x*是無訊息的 NaN、不定或無限大，則會傳回相同的值。

|Input|SEH 例外狀況|**_matherr**異常|
|-----------|-------------------|--------------------------|
|± QNAN、IND、INF|none|none|

## <a name="remarks"></a>備註

當您使用C++時，您可以呼叫採用並傳回**float**或**long** **double**值之**asinh**的多載。 在 C 程式中， **asinh**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|函數|必要的 C 標頭|必要的 C++ 標頭|
|--------------|--------------|------------------|
|**asinh**、 **asinhf**、 **asinhl**|\<math.h>|\<h > 或\<math <|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh、coshf、coshl](cosh-coshf-coshl.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
