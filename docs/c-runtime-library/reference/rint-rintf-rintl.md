---
title: rint、rintf、rintl
ms.date: 04/05/2018
api_name:
- rintf
- rintl
- rint
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
- rintf
- rintl
- rint
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
ms.openlocfilehash: ac9db3ee5a50bb334754a8a1191638a319829b97
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170887"
---
# <a name="rint-rintf-rintl"></a>rint、rintf、rintl

將浮點值四捨五入為最接近的整數，並使用浮點格式。

## <a name="syntax"></a>語法

```C
double rint( double x );
float rintf( float x );
long double rintl( long double x );
```

```cpp
float rint( float x );  // C++ only
long double rint( long double x );  // C++ only
```

### <a name="parameters"></a>參數

*x*<br/>
要四捨五入的浮點值。

## <a name="return-value"></a>傳回值

**Rint**函式會傳回浮點值，表示最接近*x*的整數。 中間值會根據浮點舍入模式的目前設定進行舍入，與**nearbyint**函數相同。 與**nearbyint**函式不同的是，如果結果與引數的值不同， **rint**函數可能會引發**FE_INEXACT**浮點例外狀況。 不會傳回錯誤。

|輸入|SEH 例外狀況|**_matherr**異常|
|-----------|-------------------|--------------------------|
|±∞、QNAN、IND|無|無|
|非正規數|EXCEPTION_FLT_UNDERFLOW|無|

## <a name="remarks"></a>備註

因為C++允許多載，所以您可以呼叫採用並傳回**浮點**和**長** **雙精度**值之**rint**的多載。 在 C 程式中， **rint**一律會採用並傳回**雙精度浮點數**。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**rint**、 **rintf**、 **rintl**|\<math.h>|\<cmath>|

如需其他相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_rint.c
// Build with: cl /W3 /Tc crt_rint.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("rint(%f) is %.0f\n", x, rint (x));
   printf("rint(%f) is %.0f\n", -x, rint (-x));
   printf("rintf(%f) is %.0f\n", y, rintf(y));
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));
}
```

```Output
rint(2.499999) is 2
rint(-2.499999) is -2
rintf(2.800000) is 3
rintf(-2.800000) is -3
rintl(2.500000) is 3
rintl(-2.500000) is -3
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround、lroundf、lroundl、llround、llroundf、llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint](rint-rintf-rintl.md)<br/>
