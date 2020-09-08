---
title: sinh、sinhf、sinhl
description: 用於計算浮點值之雙曲正弦值的 API 參考。
ms.date: 08/31/2020
api_name:
- sinh
- sinhl
- sinhf
- sinhl
- _o_sinh
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
- sinh
- sinhf
- sinhl
helpviewer_keywords:
- sinh function
- sinhl function
- sinhf function
- calculating hyperbolic sines
- trigonometric functions
- sinhf function
- sinhl function
- hyperbolic functions
ms.openlocfilehash: 6a8c9c4195eab66a46230e7a3baf6194e17c4519
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556173"
---
# <a name="sinh-sinhf-sinhl"></a>sinh、sinhf、sinhl

計算雙曲正弦值。

## <a name="syntax"></a>語法

```C
double sinh(double x);
float sinhf(float x);
long double sinhl(long double x);
#define sinh(x) // Requires C11 or higher

float sinh(float x);  // C++ only
long double sinh(long double x);  // C++ only
```

### <a name="parameters"></a>參數

*X*\
角度 (弧度)。

## <a name="return-value"></a>傳回值

**Sinh**函式會傳回*x*的雙曲正弦函數。 根據預設，如果結果太大， **sinh** 會將 **Errno** 設定為 **ERANGE** ，並傳回±**HUGE_VAL**。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± QNAN、IND|無|_DOMAIN|
|&#124;x&#124; ≥ 7.104760 e + 002|OVERFLOW+INEXACT|OVERFLOW|

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回或值的 **sinh** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **sinh** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `sinh()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-|-|-|
|**sinh**、 **sinhf**、 **sinhl**|\<math.h>|\<cmath> 或 \<math.h>|
|**sinh ( # B1 ** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_sinhcosh.c
// This program displays the hyperbolic
// sine and hyperbolic cosine of pi / 2.
// Compile by using: cl /W4 crt_sinhcosh.c

#include <math.h>
#include <stdio.h>

int main( void)
{
   double pi = 3.1415926535;
   double x, y;

   x = pi / 2;
   y = sinh( x );
   printf( "sinh( %f ) = %f\n",x, y );
   y = cosh( x );
   printf( "cosh( %f ) = %f\n",x, y );
}
```

```Output
sinh( 1.570796 ) = 2.301299
cosh( 1.570796 ) = 2.509178
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh、coshf、coshl](cosh-coshf-coshl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
