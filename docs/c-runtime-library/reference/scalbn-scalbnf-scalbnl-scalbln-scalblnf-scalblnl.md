---
title: scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl
ms.date: 4/2/2020
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
- _o_scalbln
- _o_scalblnf
- _o_scalblnl
- _o_scalbn
- _o_scalbnf
- _o_scalbnl
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d0c7f6db7ad6970be85203eef76e5ccb152e2200
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332592"
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

*X.*<br/>
浮點值。

*exp*<br/>
整數指數。

## <a name="return-value"></a>傳回值

**scalbn**函數在成功時返回*x* \* **FLT_RADIX**<sup>exp</sup>的值。 在溢出(取決於*x*的符號 **),scalbn**傳回 +/- **HUGE_VAL**;**errno**值設定為**ERANGE**。

有關**errno**與可能的錯誤傳回值的詳細資訊,請參閱[errno、_doserrno、_sys_errlist 和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**FLT_RADIX**\<在 float.h>定义为本机浮点半径;在二進位系統上,它的值為 2,**而 scalbn**等效於[ldexp](ldexp.md)。

由於C++允許重載,因此可以調用帶和返回**浮點**或**長****雙**類型的**scalbn**和**scalbln**的重載。 在C程式中 **,scalbn**總是需要**一個雙**和一**個int,** 並傳回一**個雙**,和**scalbln**總是需要**一個雙**和**長**,並傳回一**個雙**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**斯卡爾本**,**斯卡爾布夫**,**斯卡爾布恩**,**斯卡爾布恩**,**斯卡爾布恩,****斯卡爾布恩**|\<math.h>|\<cmath>|

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

### <a name="output"></a>輸出

```Output
6.4 times FLT_RADIX to the power of 3 is 51.2
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
