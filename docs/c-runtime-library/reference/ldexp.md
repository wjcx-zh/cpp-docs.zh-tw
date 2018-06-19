---
title: ldexp ldexpf，ldexpl |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
dev_langs:
- C++
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 012315e11ccf2dbe63e32c6208487f324ef29289
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401411"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp ldexpf ldexpl

將浮點數與 2 的整數冪相乘。

## <a name="syntax"></a>語法

```C
double ldexp(
   double x,
   int exp
);
float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

*exp*<br/>
整數指數。

## <a name="return-value"></a>傳回值

**Ldexp**函式傳回的值*x* * 2<sup>*exp* </sup>如果成功的話。 溢位且根據正負號的*x*， **ldexp**傳回 + /- **HUGE_VAL**; **errno**值設定為**為 ERANGE**.

如需有關**errno**和可能的錯誤，傳回值，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**ldexp**採用**float**或**長** **double**型別。 在 C 程式中， **ldexp**一律採用**double**和**int**並傳回**double**。

## <a name="requirements"></a>需求

|常式|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**ldexp**， **ldexpf**， **ldexpl**|\<math.h>|\<cmath>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>輸出

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
