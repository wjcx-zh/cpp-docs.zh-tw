---
title: tgamma、tgammaf、tgammal
ms.date: 4/2/2020
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
ms.openlocfilehash: f38ae3f3ad38eeb9806803fd8dad1b8297393168
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218516"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal

判斷指定值的 gamma 函式。

## <a name="syntax"></a>語法

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
要尋找其 gamma 的值。

## <a name="return-value"></a>傳回值

如果成功，會傳回*x*的 gamma。

如果*x*的大小對資料類型而言太大或太小，則可能會發生範圍錯誤。 如果*x* <= 0，可能會發生網域錯誤或範圍錯誤。

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

因為 c + + 允許多載，所以您可以呼叫採用並傳回和類型之**tgamma**的多載 **`float`** **`long double`** 。 在 C 程式中， **tgamma**一律會採用並傳回 **`double`** 。

如果 x 為自然數，此函式會傳回 (x-1) 階乘。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**tgamma**、 **tgammaf**、 **tgammal**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
