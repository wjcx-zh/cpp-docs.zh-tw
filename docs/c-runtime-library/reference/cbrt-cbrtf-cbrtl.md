---
title: cbrt、cbrtf、cbrtl
ms.date: 04/05/2018
api_name:
- cbrt
- cbrtf
- cbrtl
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
- cbrtl
- cbrt
- cbrtf
helpviewer_keywords:
- cbrtl function
- cbrtf function
- cbrt function
ms.assetid: ab51d916-3db2-4beb-b46a-28b4062cd33f
ms.openlocfilehash: d3983c5d3237b1a6cb82887a690919cbf21401ab
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939296"
---
# <a name="cbrt-cbrtf-cbrtl"></a>cbrt、cbrtf、cbrtl

計算立方根。

## <a name="syntax"></a>語法

```C
double cbrt(
   double x
);
float cbrt(
   float x
);  // C++ only
long double cbrt(
   long double x
);  // C++ only
float cbrtf(
   float x
);
long double cbrtl(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**Cbrt**函數會傳回*x*的 cube 根。

|Input|SEH 例外狀況|**_matherr**異常|
|-----------|-------------------|--------------------------|
|±∞、QNAN、IND|none|none|

## <a name="remarks"></a>備註

因為C++允許多載，所以您可以呼叫採用**float**或**long** **double**類型之**cbrt**的多載。 在 C 程式中， **cbrt**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**cbrt**、 **cbrtf**、 **cbrtl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cbrt.c
// Compile using: cl /W4 crt_cbrt.c
// This program calculates a cube root.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double question = -64.64;
   double answer;

   answer = cbrt(question);
   printf("The cube root of %.2f is %.6f\n", question, answer);
}
```

```Output
The cube root of -64.64 is -4.013289
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
