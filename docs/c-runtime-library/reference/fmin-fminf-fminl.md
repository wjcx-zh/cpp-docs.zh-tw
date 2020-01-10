---
title: fmin、fminf、fminl
ms.date: 04/05/2018
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
ms.openlocfilehash: df01f2205291920b8c0519db622c93048278beb1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957085"
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
```

### <a name="parameters"></a>參數

*x*<br/>
要比較的第一個值。

*y*<br/>
要比較的第二個值。

## <a name="return-value"></a>傳回值

如果成功，會傳回*x*或*y*的較小者。

|Input|結果|
|-----------|------------|
|*x*是 NaN|*y*|
|*y*是 NaN|*x*|
|*x*和*y*是 NaN|NaN|

函式不會導致叫用[_matherr](matherr.md) 、造成任何浮點例外狀況，或變更**errno**的值。

## <a name="remarks"></a>備註

因為C++允許多載，所以您可以呼叫採用並傳回**float**和**long** **double**類型之**fmin**的多載。 在 C 程式中， **fmin**一律會採用並傳回**雙精度浮點數**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**fmin**、 **fminf**、 **fminl**|C：\<math.h><br />C++：\<math.h> 或 \<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
