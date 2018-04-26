---
title: exp2、exp2f、exp2l | Microsoft Docs
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
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
dev_langs:
- C++
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69b7deb8e6e43ded0a3545bc1b33961d977eeb1f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="exp2-exp2f-exp2l"></a>exp2、exp2f、exp2l

計算 2 的乘至指定的值。

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
```

### <a name="parameters"></a>參數

*x*<br/>
指數值。

## <a name="return-value"></a>傳回值

如果成功，傳回的基底 2 指數*x*，也就是 2<sup>x</sup>。 否則，它會傳回下列值之一：

|問題|Return|
|-----------|------------|
|*x* = ±0|1|
|*x* =-INFINITY|+0|
|*x* = + INFINITY|+INFINITY|
|*x* = NaN|NaN|
|溢位範圍錯誤|+HUGE_VAL、+HUGE_VALF 或 +HUGE_VALL|
|反向溢位範圍錯誤|正確的結果，四捨五入之後|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**exp2**採用並傳回**float**和**長雙精度**型別。 在 C 程式中， **exp2**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**exp**， **expf**，**總管**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
