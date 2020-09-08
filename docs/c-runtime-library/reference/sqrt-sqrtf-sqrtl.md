---
title: sqrt、sqrtf、sqrtl
description: Sqrt、sqrtf 和 sqrtl 的 API 參考;這會計算浮點數的平方根。
ms.date: 08/31/2020
api_name:
- sqrtl
- sqrtf
- sqrt
- _o_sqrt
- _o_sqrtf
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 17526b4e4a7eca5d36c01069dbe975bb035d1f58
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556771"
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
#define sqrt(x) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
非負值浮點值

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用或類型之 **sqrt** 的多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **sqrt** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `sqrt()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="return-value"></a>傳回值

**Sqrt**函數會傳回*x*的平方根。 依預設，如果 *x* 是負數， **sqrt** 會傳回不定的 NaN。

|輸入|SEH 例外狀況|**_matherr** 例外|
|-----------|-------------------|--------------------------|
|± QNAN、IND|無|_DOMAIN|
|- ∞|無|_DOMAIN|
|x<0|無|_DOMAIN|

## <a name="requirements"></a>規格需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**sqrt**、 **sqrtf**、 **sqrtl**|\<math.h>|\<cmath>|
|**sqrt ( # B1 ** 宏 | \<tgmath.h> ||

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
