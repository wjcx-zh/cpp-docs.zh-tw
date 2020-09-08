---
title: exp2、exp2f、exp2l
description: '適用于 exp2 的 API ref ( # A1、exp2f ( # A3 和 exp2l ( # A5，其計算2會提高為指定的值。'
ms.date: 9/1/2020
api_name:
- exp2
- exp2f
- exp2l
- _o_exp2
- _o_exp2f
- _o_exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 518525a38ef575583fde3b7732561f2fa553dd18
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556615"
---
# <a name="exp2-exp2f-exp2l"></a>exp2、exp2f、exp2l

計算2會引發為指定的值。

## <a name="syntax"></a>語法

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
#define exp2(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
指數值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x*的底數2指數，也就是 2<sup>x</sup>。 否則，它會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* = ±0|1|
|*x* =-無限大|+0|
|*x* = + 無限大|+INFINITY|
|*x* = NaN|NaN|
|溢位範圍錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|
|反向溢位範圍錯誤|舍入後的正確結果|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **exp2** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您使用 \<tgmath.h> 宏來呼叫這個函式，否則 **exp2** 一律會採用並傳回 **`double`** ，除非您在 <> >tgmath.h> 中使用宏。

如果您使用 \<tgmath.h> `exp2()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**exp2**、 **expf2**、 **expl2**|\<math.h>|\<cmath>|
|**exp2** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
