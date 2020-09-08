---
title: fmax、fmaxf、fmaxl
description: Fmax、fmaxf 和 fmaxl 的 API 參考;這會決定兩個數值的較大值。
ms.date: 9/1/2020
api_name:
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 4f38db64b30598e7cfb4eb4d0f57dccf257dabc5
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556680"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax、fmaxf、fmaxl

決定兩個指定數值的較大者。

## <a name="syntax"></a>語法

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

#define fmax(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
要比較的第一個值。

*Y*\
要比較的第二個值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x* 或 *y*的較大。 傳回的值會完全相同，而且不是取決於任何形式的四捨五入。

否則，可能會傳回下列其中一個值：

|問題|傳回|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* 和 *y* = NaN|NaN|

此函式不會使用 [_matherr](matherr.md) 中所指定的錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 fmax 多載 `float` `long double` 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 `fmax` 一律會採用並傳回雙精度浮點數。

如果您使用 \<tgmath.h> `fmax()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fmax**、 **fmaxf**、 **fmaxl**|\<math.h>|\<cmath> 或 \<math.h>|
|**fmax** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[fmin、fminf、fminl](fmin-fminf-fminl.md)<br/>
