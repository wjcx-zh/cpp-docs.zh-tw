---
title: fmin、fminf、fminl
description: Fmin、fminf 和 fminl 的 API 參考;這會決定兩個值中較小的一個。
ms.date: 9/1/2020
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: 6a070835d809c6adcb5b7bfd57b5373886b348ca
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556706"
---
# <a name="fmin-fminf-fminl"></a>fmin、fminf、fminl

決定兩個指定值的較小者。

## <a name="syntax"></a>語法

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);

#define fmin(x) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
要比較的第一個值。

*Y*\
要比較的第二個值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x* 或 *y*的較小者。

|輸入|結果|
|-----------|------------|
|*x* 是 NaN|*y*|
|*y* 是 NaN|*x*|
|*x* 和 *y* 是 NaN|NaN|

函數不會導致叫用 [_matherr](matherr.md) 、導致任何浮點例外狀況，或變更 **errno**的值。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **fmin** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **fmin** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `fmin()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**fmin**、 **fminf**、 **fminl**|C： \<math.h><br />C + +： \<math.h> 或 \<cmath>|
|**fmin** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
