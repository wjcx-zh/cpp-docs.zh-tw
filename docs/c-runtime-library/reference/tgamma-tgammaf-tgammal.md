---
title: tgamma、tgammaf、tgammal
description: Tgamma、tgammaf 和 tgammal 的 API 參考;判斷指定值的 gamma 函數。
ms.date: 9/1/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: b49020ca0697e920dccf188df4ad024820966571
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555172"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal

判斷指定值的 gamma 函式。

## <a name="syntax"></a>語法

```C
double tgamma(
   double x
);

float tgammaf(
   float x
);

long double tgammal(
   long double x
);

#define tgamma(X) // Requires C11 or higher

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only
```

### <a name="parameters"></a>參數

*X*\
要尋找其 gamma 的值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x*的 gamma。

如果 *x* 的大小對資料類型而言太大或太小，則可能會發生範圍錯誤。 如果 *x* <= 0，則可能會發生網域錯誤或範圍錯誤。

|問題|傳回|
|-----------|------------|
|x = ±0|±無限大|
|x = 負整數|NaN|
|x =-無限大|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|網域錯誤|NaN|
|極錯誤|± HUGE_VAL、± HUGE_VALF 或± HUGE_VALL|
|溢位範圍錯誤|± HUGE_VAL、± HUGE_VALF 或± HUGE_VALL|
|反向溢位範圍錯誤|正確的值 (四捨五入後)。|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **tgamma** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **tgamma** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `tgamma()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

如果 x 為自然數，此函式會傳回 (x-1) 階乘。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**tgamma**、 **tgammaf**、  **tgammal**|\<math.h>|\<cmath>|
|**tgamma** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
