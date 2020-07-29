---
title: fdim、fdimf、fdiml
ms.date: 04/05/2018
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
ms.openlocfilehash: 1a7bbeaf77c94f620a82f77fb1aad3c71c34f2ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221909"
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
```

### <a name="parameters"></a>參數

*x*<br/>
第一個值。

*y*<br/>
第二個值。

## <a name="return-value"></a>傳回值

傳回*x*和*y*之間的正差：

|傳回值|案例|
|------------------|--------------|
|x-y|如果 x > y|
|0|如果 x <= y|

否則，可能會傳回下列一項錯誤：

|問題|傳回|
|-----------|------------|
|溢位範圍錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|
|反向溢位範圍錯誤|正確的值 (四捨五入後)|
|*x*或*y*是 NaN|NaN|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用並傳回和類型之**fdim**的多載 **`float`** **`long double`** 。 在 C 程式中， **fdim**一律會採用並傳回 **`double`** 。

除了 NaN 處理之外，此函式相當於 `fmax(x - y, 0)` 。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fdim**、 **fdimf**、 **fdiml**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
