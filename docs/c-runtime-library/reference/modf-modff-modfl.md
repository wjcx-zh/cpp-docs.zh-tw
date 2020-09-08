---
title: modf、modff、modfl
description: Modf、modff 和 modfl 的 API 參考;這會將浮點值分割成小數和整數部分。
ms.date: 4/2/2020
api_name:
- modff
- modf
- modfl
- _o_modf
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 0d3522079acc8a9d2c8409b1cad78e7f50a7f788
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556758"
---
# <a name="modf-modff-modfl"></a>modf、modff、modfl

將浮點值分割成小數和整數部分。

## <a name="syntax"></a>語法

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

*intptr*<br/>
儲存之整數部分的指標。

## <a name="return-value"></a>傳回值

此函式會傳回 *x* 的帶正負號小數部分。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Modf**函式會將浮點值*x*細分成小數和整數部分，每個部分都具有與*x*相同的正負號。 會傳回 *x* 的帶正負號小數部分。 整數部分會儲存為 *intptr*的浮點值。

**modf** 具有使用 Streaming SIMD Extensions 2 (SSE2) 的實作為。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

C + + 允許多載，所以您可以呼叫採用和傳回或參數的 **modf** 多載 **`float`** **`long double`** 。 在 C 程式中， **modf** 一律採用兩個雙精度值，並傳回雙精度浮點數。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**modf**、 **modff**、 **modfl**|C： \<math.h><br /><br /> C + +： \<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
