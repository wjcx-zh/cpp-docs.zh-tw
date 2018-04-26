---
title: fmod、 fmodf，fmodl |Microsoft 文件
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fmod
- fmodf
- fmodl
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
- fmod
- _fmodl
- fmodf
dev_langs:
- C++
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c31ec67e3b5c75c334a985461365c7b139758427
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="fmod-fmodf-fmodl"></a>fmod、 fmodf fmodl

計算浮點餘數。

## <a name="syntax"></a>語法

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>參數

*x*， *y*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**fmod**傳回浮點餘數*x* / *y*。 如果值*y*為 0.0， **fmod**傳回無訊息 NaN。 如需無訊息 NaN 的表示法**printf**系列，請參閱[printf](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**Fmod**函式會計算浮點數餘數*f*的*x* / *y*使得*x* = *我* * *y* + *f*，其中*我*是整數， *f*具有相同的簽章為*x*，和數值的絕對值*f*數值的絕對值小於*y*。

C + + 允許多載，所以您可以呼叫的多載**fmod**採用並傳回**float**和**長** **double**值。 在 C 程式中， **fmod**一律會採用兩個**double**引數並傳回**double**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fmod**， **fmodf**， **fmodl**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
