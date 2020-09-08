---
title: exp、expf、expl
description: Exp、expf 和 expl 的 API 參考;計算指數的。
ms.date: 08/31/2020
api_name:
- expf
- expl
- exp
- _o_exp
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
ms.openlocfilehash: 44652e5d06d842bd2eb2e280409a1e55fc66f582
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555887"
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
#define exp(z) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
用來 exponentiate 自然對數底數 *e* 的浮點值。

## <a name="return-value"></a>傳回值

如果成功， **exp** 函數會傳回浮點參數 *x*的指數值。 也就是說，結果是 *e*<sup>*x*</sup>，其中 *e* 是自然對數的基底。 溢位時，此函數會傳回 INF (無限大) 和在下溢時， **exp** 會傳回0。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± Quiet NaN、不定|無|_DOMAIN|
|±無限大|無效|_DOMAIN|
|x ≥ 7.097827e+002|INEXACT+OVERFLOW|OVERFLOW|
|X ≤ -7.083964e+002|INEXACT+UNDERFLOW|UNDERFLOW|

**Exp**函式具有使用 Streaming SIMD Extensions 2 (SSE2) 的實作為。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](set-sse2-enable.md)。

## <a name="remarks"></a>備註

C + + 允許多載，所以您可以**exp**呼叫採用 **`float`** 或引數的 exp 的多載 **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函數，否則 **exp** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `exp()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的 C 標頭|必要的 C++ 標頭|
|--------------|---------------------|---|
|**exp**、 **expf**、 **expl**|\<math.h>|\<cmath> 或 \<math.h>|
|**exp** 宏| \<tgmath.h> || 

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
