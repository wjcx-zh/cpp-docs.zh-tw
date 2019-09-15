---
title: scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl
ms.date: 04/05/2018
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
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
- scalblnf
- scalbnl
- scalblnl
- scalbln
- scalbn
- scalbnf
helpviewer_keywords:
- scalbn function
- scalbln function
- scalblnl function
- scalbnl function
- scalbnf function
- scalblnf function
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
ms.openlocfilehash: 794d0bdceb13aafb83de85fb29e47a4fa3125cd6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948906"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl

將浮點數與 FLT_RADIX 的整數冪相乘。

## <a name="syntax"></a>語法

```C
double scalbn(
   double x,
   int exp
);
float scalbn(
   float x,
   int exp
);  // C++ only
long double scalbn(
   long double x,
   int exp
);  // C++ only
float scalbnf(
   float x,
   int exp
);
long double scalbnl(
   long double x,
   int exp
);
double scalbln(
   double x,
   long exp
);
float scalbln(
   float x,
   long exp
);  // C++ only
long double scalbln(
   long double x,
   long exp
);  // C++ only
float scalblnf(
   float x,
   long exp
);
long double scalblnl(
   long double x,
   long exp
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

*exp*<br/>
整數指數。

## <a name="return-value"></a>傳回值

當成功時， **scalbn**函數會傳回*x* \* **FLT_RADIX**<sup>exp</sup>的值。 溢位時（視*x*的正負號而定）， **scalbn**會傳回 +/- **HUGE_VAL**;**errno**值會設定為**ERANGE**。

如需**errno**和可能的錯誤傳回值的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**FLT_RADIX**是在 float \<. > h 中定義成原生浮點基數，在二進位系統上，其值為2，而**scalbn**相當於[ldexp](ldexp.md)。

因為C++允許多載，所以您可以呼叫採用並傳回**float**或**long** **double**類型的**scalbn**和**scalbln**多載。 在 C 程式中， **scalbn**一律採用**double**和**int** ，並傳回**double**，而**scalbln**一律採用**double**和**long** ，並傳回**雙精度**浮點數。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**scalbn**、 **scalbnf**、 **scalbnl**、 **scalbln**、 **scalblnf**、 **scalblnl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_scalbn.c
// Compile using: cl /W4 crt_scalbn.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 6.4, y;
   int p = 3;

   y = scalbn( x, p );
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );
}
```

### <a name="output"></a>Output

```Output
6.4 times FLT_RADIX to the power of 3 is 51.2
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
