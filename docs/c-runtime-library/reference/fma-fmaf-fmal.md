---
title: fma、fmaf、fmal
description: Fma、fmaf 和 fmal 的 API 參考;這會將兩個值相乘，並加入第三個值，然後四捨五入結果，而不會因為中繼舍入而遺失任何精確度。
ms.date: 9/1/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: e9ae92c28f24b6281d73450c7cabaad775a84d42
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556693"
---
# <a name="fma-fmaf-fmal"></a>fma、fmaf、fmal

將兩個值相乘，並加入第三個值，然後四捨五入結果，而不會因為中繼舍入而遺失任何精確度。

## <a name="syntax"></a>語法

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);

#define fma(X, Y, Z) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
要相乘的第一個值。

*Y*\
要相乘的第二個值。

*Z*\
要加入的值。

## <a name="return-value"></a>傳回值

傳回 `(x * y) + z`。 傳回值接著會使用目前的四捨五入格式來進行四捨五入。

否則，可能會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* = 無限大、 *y* = 0 或<br /><br /> *x* = 0、 *y* = 無限大|NaN|
|*x* 或 *y* = 精確的±無限大， *z* = 無限大且正負號相反|NaN|
|*x* 或 *y* = NaN|NaN|
|不 (*x* = 0、 *y*= 不定) 和 *z* = NaN<br /><br /> 不 (*x*= 不定、 *y*= 0) 和 *z* = NaN|NaN|
|溢位範圍錯誤|± HUGE_VAL、± HUGE_VALF 或± HUGE_VALL|
|反向溢位範圍錯誤|四捨五入後的正確值。|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回類型之 **fma** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函數，否則 **fma** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `fma()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

此函式會計算值，就像它採用無限精確度，然後將最終結果進行四捨五入。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fma**、 **fmaf**、 **fmal**|\<math.h>|\<cmath>|
|**fma** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[remainder、remainderf、remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
