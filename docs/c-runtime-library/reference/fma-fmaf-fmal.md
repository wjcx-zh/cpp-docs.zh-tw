---
title: fma、fmaf、fmal
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 993ca4d57202b3789929161a964b3e41d48fd98f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346561"
---
# <a name="fma-fmaf-fmal"></a>fma、fmaf、fmal

將兩個值相乘，並加上第三個值，然後對結果進行四捨五入，而且不會因中值四捨五入而遺失任何精確度。

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
```

### <a name="parameters"></a>參數

*X.*<br/>
要相乘的第一個值。

*Y*<br/>
要相乘的第二個值。

*Z*<br/>
要加入的值。

## <a name="return-value"></a>傳回值

傳回 `(x * y) + z`。 傳回值接著會使用目前的四捨五入格式來進行四捨五入。

否則，可能會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* = *INFINITY,y* = 0 或<br /><br /> *x* = *0,y* = INFINITY|NaN|
|*x*或*y* = 精確 = *INFINITY,z* = 帶相反符號的 INFINITY|NaN|
|*x*或*y* = NaN|NaN|
|不 *(x* = *0,y*= 無限期)和*z* = NaN<br /><br /> 不 *(x*=不確定 *,y*=0)和*z* = NaN|NaN|
|溢位範圍錯誤|[HUGE_VAL、HUGE_VALF 或 HUGE_VALL|
|反向溢位範圍錯誤|四捨五入後的正確值。|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

由於C++允許重載,因此可以調用獲取和返回**浮點**和**長****雙**類型的**fma**的重載。 在 C 程式中 **,fma**始終取得並傳回**一個雙**。

此函式會計算值，就像它採用無限精確度，然後將最終結果進行四捨五入。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[remainder、remainderf、remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
