---
title: tan、tanf、tanl
description: Tan、tanf 和 tanl 的 API 參考;計算浮點值的正切值。
ms.date: 08/31/2020
api_name:
- tan
- tanf
- tanl
- _o_tan
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
- tan
- tanf
- _tanl
- tanl
helpviewer_keywords:
- tanl function
- _tanl function
- tan function
- calculating tangents
- tangent
- tanf function
- trigonometric functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
ms.openlocfilehash: 8137bf4cbce59083e8e7c09557400fbff4f6b1df
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556537"
---
# <a name="tan-tanf-tanl"></a>tan、tanf、tanl

計算正切函數。

## <a name="syntax"></a>語法

```C
double tan( double x );
float tanf( float x );
long double tanl( long double x );
#define tan(x) // Requires C11 or higher
```

```cpp
float tan( float x );  // C++ only
long double tan( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*X*\
角度 (弧度)。

## <a name="return-value"></a>傳回值

**Tan**函式會傳回*x*的正切函數。 如果 *x* 大於或等於263，或小於或等於-263，則結果中會遺失精確度。

|輸入|SEH 例外狀況|**Matherr** 例外|
|-----------|-------------------|-------------------------|
|± QNAN、IND|無|_DOMAIN|
|± INF|**無效**|_DOMAIN|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回或值的 **tan** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **tan** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `tan()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------|-|
|**tan**、 **tanf**、 **tanl**|\<math.h>|\<cmath> 或 \<math.h>|
|**tan ( # B1 ** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_tan.c
// This program displays the tangent of pi / 4
// Compile by using: cl crt_tan.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x;

   x = tan( pi / 4 );
   printf( "tan( %f ) = %f\n", pi/4, x );
}
```

```Output
tan( 0.785398 ) = 1.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[_CItan](../../c-runtime-library/citan.md)<br/>
