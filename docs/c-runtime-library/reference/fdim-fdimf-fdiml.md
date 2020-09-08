---
title: fdim、fdimf、fdiml
description: Fdim、fdimf 和 fdiml 的 API 參考;這會決定兩個值之間的正差。
ms.date: 9/1/2020
api_name:
- fdim
- fdimf
- fdiml
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 406fc5cfe543aa0865760df9ff780c62e78510fc
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554782"
---
# <a name="fdim-fdimf-fdiml"></a>fdim、fdimf、fdiml

判斷第一個和第二個值之間的正差。

## <a name="syntax"></a>語法

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);

#define fdim(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
第一個值。

*Y*\
第二個值。

## <a name="return-value"></a>傳回值

傳回 *x* 和 *y*之間的正差：

|傳回值|案例|
|------------------|--------------|
|x-y|如果 x > y|
|0|如果 x <= y|

否則，可能會傳回下列一項錯誤：

|問題|傳回|
|-----------|------------|
|溢位範圍錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|
|反向溢位範圍錯誤|正確的值 (四捨五入後)|
|*x* 或 *y* 是 NaN|NaN|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **fdim** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **fdim** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `fdim()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

除了 NaN 處理之外，此函數相當於 `fmax(x - y, 0)` 。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fdim**、 **fdimf**、 **fdiml**|\<math.h>|\<cmath>|
|**fdim** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
