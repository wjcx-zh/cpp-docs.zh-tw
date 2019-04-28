---
title: fmax、fmaxf、fmaxl
ms.date: 04/05/2018
apiname:
- fmax
- fmaxf
- fmaxl
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 371d53257427f2235048807968c82fec1b8bf699
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333427"
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
```

### <a name="parameters"></a>參數

*x*<br/>
要比較的第一個值。

*y*<br/>
要比較的第二個值。

## <a name="return-value"></a>傳回值

如果成功，傳回的較大*x*或是*y*。 傳回的值會完全相同，而且不是取決於任何形式的四捨五入。

否則，可能會傳回下列其中一個值：

|問題|Return|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x*並*y* = NaN|NaN|

此函式不會使用 [_matherr](matherr.md) 中所指定的錯誤。

## <a name="remarks"></a>備註

因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點數和長雙精度浮點數類型之 fmax 的多載。 在 C 程式中，fmax 一律會採用並傳回雙精度浮點數。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**fmax**， **fmaxf**， **fmaxl**|\<math.h>|\<cmath> 或 \<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fmin、fminf、fminl](fmin-fminf-fminl.md)<br/>
