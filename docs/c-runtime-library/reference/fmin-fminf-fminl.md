---
title: fmin fminf，fminl |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fmin
- fminf
- fminl
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
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3de46ba0a8d550d961fd05527b49a68a1518c50a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

如果成功，傳回較小的*x*或*y*。

|輸入|結果|
|-----------|------------|
|*x*是 NaN|*y*|
|*y*是 NaN|*x*|
|*x*和*y*是 NaN|NaN|

此函式不會造成[_matherr](matherr.md)叫用時，會造成任何浮點例外狀況，或變更的值**errno**。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**fmin**採用並傳回**float**和**長** **double**型別。 在 C 程式中， **fmin**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**fmin**， **fminf**， **fminl**|C：\<math.h><br />C++：\<math.h> 或 \<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
