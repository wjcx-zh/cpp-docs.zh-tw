---
title: atan、atanf、atanl、atan2、atan2f、atan2l
ms.date: 04/05/2018
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: 59a67b0d213a11630f551fd7582b44aab60e314f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341713"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan、atanf、atanl、atan2、atan2f、atan2l

計算反正切**x** (**atan**， **atanf**，以及**atanl**) 或反正切值**y** /**x** (**atan2**， **atan2f**，以及**atan2l**)。

## <a name="syntax"></a>語法

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*， *y*<br/>
任何數字。

## <a name="return-value"></a>傳回值

**atan**傳回的反正切*x*範圍-π/2 到 π/2 弧度。 **atan2**傳回的反正切*y*/*x*中範圍-π 到 π 弧度。 如果*x*為 0， **atan**會傳回 0。 如果這兩個參數的**atan2**都是 0，則函數會傳回 0。 所有結果都以弧度為單位。

**atan2**會使用這兩個參數的符號來判斷傳回值的象限。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|常见**QNAN**， **IND**|none|**_DOMAIN**|

## <a name="remarks"></a>備註

**Atan**函式會計算反正切值 （反向 tangent 函式） 的*x*。 **atan2**計算反正切*y*/*x* (如果*x*等於 0， **atan2**傳回 π/2，如果*y*是正數，-π/2; 如果*y*為負值或 0 *y*為 0。)

**atan**有使用 Streaming SIMD Extensions 2 (SSE2) 的實作。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

因為C++允許多載，您可以呼叫多載**atan**並**atan2**採用**float**或**長** **double**引數。 在 C 程式中， **atan**並**atan2**蝯篔**double**引數和傳回**double**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**atan**， **atan2**， **atanf**， **atan2f**， **atanl**， **atan2l**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="example"></a>範例

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
