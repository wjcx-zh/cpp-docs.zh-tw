---
title: atanh、atanhf、atanhl
description: Atanh、atanhf 和 atanhl 的 API 參考;計算浮點值的反雙曲正切值。
ms.date: 08/31/2020
api_name:
- atanhl
- atanhf
- atanh
- _o_atanh
- _o_atanhf
- _o_atanhl
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
- atanhl
- atanhf
- atanh
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
ms.openlocfilehash: c0a8e06963519553144c7e49d26e61dbbde51c21
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555588"
---
# <a name="atanh-atanhf-atanhl"></a>atanh、atanhf、atanhl

計算反雙曲正切。

## <a name="syntax"></a>語法

```C
double atanh( double x );
float atanhf( float x );
long double atanhl( long double x );
#define atanh(X) // Requires C11 or higher

float atanh( float x );  // C++ only
long double atanh( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*X*\
浮點值。

## <a name="return-value"></a>傳回值

**Atanh**函式會傳回反向雙曲正切 (*x*的弧線雙曲正切函數) 。 如果 *x* 大於1或小於-1，則 **errno** 會設定為 **EDOM** ，且結果為無訊息 NaN。 如果 *x* 等於1或-1，則會分別傳回正或負無限大，且 **errno** 會設定為 **ERANGE**。

|輸入|SEH 例外狀況|**Matherr** 例外|
|-----------|-------------------|-------------------------|
|± QNAN、IND|無|無|
|*X* ≥ 1; *x* ≤-1|無|無|

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回或值的 **atanh** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **atanh** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `atanh()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**atanh**、 **atanhf**、 **atanhl**|\<math.h>|\<cmath> 或 \<math.h>|
|**atanh ( # B1 ** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_atanh.c
// This program displays the hyperbolic tangent of pi / 4
// and the arc hyperbolic tangent of the result.
//

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tanh( pi / 4 );
   y = atanh( x );
   printf( "tanh( %f ) = %f\n", pi/4, x );
   printf( "atanh( %f ) = %f\n", x, y );
}
```

```Output
tanh( 0.785398 ) = 0.655794
atanh( 0.655794 ) = 0.785398
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[cosh、coshf、coshl](cosh-coshf-coshl.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
