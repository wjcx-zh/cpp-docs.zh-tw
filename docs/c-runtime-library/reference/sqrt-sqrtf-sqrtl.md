---
title: sqrt、sqrtf、sqrtl
ms.date: 4/2/2020
api_name:
- sqrtl
- sqrtf
- sqrt
- _o_sqrt
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- sqrt
- sqrtf
- _sqrtl
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
ms.openlocfilehash: 364db84bc20f9f6cfafbdc53e1f2df6da70592df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355574"
---
# <a name="sqrt-sqrtf-sqrtl"></a>sqrt、sqrtf、sqrtl

計算平方根。

## <a name="syntax"></a>語法

```C
double sqrt(
   double x
);
float sqrt(
   float x
);  // C++ only
long double sqrt(
   long double x
);  // C++ only
float sqrtf(
   float x
);
long double sqrtl(
   long double x
);
```

### <a name="parameters"></a>參數

*X.*<br/>
非負值浮點值

## <a name="remarks"></a>備註

由於C++允許重載,因此可以調用採用**浮點**或**長****雙**類型平方**的**重載。 在 C 程式中 **,sqrt**始終採用並返回**雙**精度 值。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="return-value"></a>傳回值

**平方函數**返回*x*的平方根。 默認情況下,如果*x*為負數 **,sqrt**將返回不確定的 NaN。

|輸入|SEH 例外狀況|**_matherr**例外|
|-----------|-------------------|--------------------------|
|• QNAN,IND|無|_DOMAIN|
|- ∞|無|_DOMAIN|
|x<0|無|_DOMAIN|

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**sqrt**, **sqrtf**, **sqrtl**|\<math.h>|\<cmath>|

如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_sqrt.c
// This program calculates a square root.

#include <math.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   double question = 45.35, answer;
   answer = sqrt( question );
   if( question < 0 )
      printf( "Error: sqrt returns %f\n", answer );
   else
      printf( "The square root of %.2f is %.2f\n", question, answer );
}
```

```Output
The square root of 45.35 is 6.73
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
