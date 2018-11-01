---
title: expm1、expm1f、expm1l
ms.date: 04/05/2018
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 5971f879ecef7d4fa1027849cc44d598e877b5f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441063"
---
# <a name="expm1-expm1f-expm1l"></a>expm1、expm1f、expm1l

計算底數為 e 的指數值減一。

## <a name="syntax"></a>語法

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點指數值。

## <a name="return-value"></a>傳回值

**Expm1**函式會傳回浮點數的值，表示電子<sup>x</sup> -1，如果成功。 溢位時， **expm1**會傳回**HUGE_VAL**， **expm1f**傳回**HUGE_VALF**， **expm1l**傳回**HUGE_VALL**，並**errno**設定為**ERANGE**。 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

因為 c + + 允許多載，您可以呼叫多載**expm1**採用並傳回**float**並**長** **double**值。 在 C 程式中， **expm1**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**expm1**， **expm1f**， **expm1l**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
