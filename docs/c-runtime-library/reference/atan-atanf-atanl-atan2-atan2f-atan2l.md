---
title: atan、atanf、atanl、atan2、atan2f、atan2l
description: Atan、atanf、atanl、atan2、atan2f 和 atan2l 的 API 參考;這會計算浮點值的反正切值。
ms.date: 08/31/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
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
ms.openlocfilehash: 1f1d33aac86d94ab3731dd5cf5b124af99ccb3f2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555627"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan、atanf、atanl、atan2、atan2f、atan2l

計算**x** (**atan**、 **atanf**和**atanl**) 的反正切值，或是**y** / **x** (**atan2**、 **atan2f**和**atan2l**) 的反正切值。

## <a name="syntax"></a>語法

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );
#define atan(X) // Requires C11 or higher

float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
#define atan2(Y, X) // Requires C11 or higher

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*、 *y*\
任何數字。

## <a name="return-value"></a>傳回值

**atan** 會傳回範圍-π/2 到π/2 弧度之間 *x* 的反正切值。 **atan2**會傳回*y* / 範圍-π到π弧度的 y*x*反正切值。 如果 *x* 是0，則 **atan** 會傳回0。 如果兩個 **atan2** 參數都是0，則函數會傳回0。 所有結果都以弧度為單位。

**atan2** 會使用這兩個參數的正負號來判斷傳回值的象限。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**、 **IND**|無|**_DOMAIN**|

## <a name="remarks"></a>備註

**Atan**函數會計算反正切函數) *x*的反正切 (。 如果 x 等於0， **atan2**會計算*y* / *x* (的反正切值; 如果*y*是正數，則**atan2**會傳回π/2 *; 如果 y*是負值，則為-π/2; 如果 y 是0，則為0。 ) *x* *y*

如果您使用 \<tgmath.h> `atan()` 或 `atan2()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

**atan** 具有使用 Streaming SIMD Extensions 2 (SSE2) 的實作為。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

因為 c + + 允許多載，所以您**atan**可以呼叫**atan2**採用 **`float`** 或引數的 atan 和 atan2 的多載 **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函式，否則 **atan** 和 **atan2** 一律會採用 **`double`** 引數，並傳回 **`double`** 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**atan**、 **atan2**、 **atanf**、 **atan2f**、 **atanl**、 **atan2l**|\<math.h>|\<cmath> 或 \<math.h>|
|**atan ( # B1 **， **atan2** 宏 | \<tgmath.h> ||

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
