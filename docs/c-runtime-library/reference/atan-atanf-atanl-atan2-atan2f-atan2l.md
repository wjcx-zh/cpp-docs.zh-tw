---
title: atan、atanf、atanl、atan2、atan2f、atan2l
ms.date: 4/2/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
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
ms.openlocfilehash: 3b8411f9839022477dff3100792e271e2f0b572b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334110"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan、atanf、atanl、atan2、atan2f、atan2l

計算**x(****阿坦**,**阿坦夫**和**阿坦爾**)的弧形或**y**/**x(****阿坦2,****阿坦 2f**和**atan2l)** 的弧形。

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

*x*, *y*<br/>
任何數字。

## <a name="return-value"></a>傳回值

**atan**返回範圍 -*/2 到 +/2 弧度中的*x*弧形。 **atan2**傳回範圍 -α 中*y*/*x*的弧線 - = 弧度。 如果*x*為 0,**則 atan**返回 0。 如果**atan2**的兩個參數均為 0,則函數返回 0。 所有結果都以弧度為單位。

**atan2**使用兩個參數的符號來確定返回值的象限。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|• **QNAN**, **IND**|無|**_DOMAIN**|

## <a name="remarks"></a>備註

**atan**函數計算*x*的弧切(逆切線函數)。 **atan2**計算*y*/*x*的弧形(如果*x*等於**0,atan2**返回 +/2,如果*y*為正,則 -+/2 如果*y*為負,則為 0,如果*y*為 0,則為 0。

**atan**具有使用流式 SIMD 擴展 2 (SSE2) 的實現。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

由於C++允許重載,因此可以調用採用**浮點**或**長****雙**參數的**atan**和**atan2**的重載。 在 C 程式中 **,atan**和**atan2**總是採用**雙重**參數並傳回**一個雙**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**阿坦**,**阿坦2**,**阿坦夫**,**阿坦2f**,**阿坦,****阿坦2l**|\<math.h>|\<cmath> 或 \<math.h>|

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
