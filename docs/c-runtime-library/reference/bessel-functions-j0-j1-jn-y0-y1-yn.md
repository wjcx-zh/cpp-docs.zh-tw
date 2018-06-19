---
title: Bessel 函式：_j0、_j1、_jn、_y0、_y1、_yn | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
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
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
dev_langs:
- C++
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf461a7737ee1f23650ff80f203524c427fb644d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393598"
---
# <a name="bessel-functions-j0-j1-jn-y0-y1-yn"></a>Bessel 函數：_j0、_j1、_jn、_y0、_y1、_yn

計算 0、1 或 n 階的第一類或第二類 Bessel 函數。 這些 Bessel 函式通常用於電磁波理論的數學運算。

## <a name="syntax"></a>語法

```C
double _j0(
   double x
);
double _j1(
   double x
);
double _jn(
   int n,
   double x
);
double _y0(
   double x
);
double _y1(
   double x
);
double _yn(
   int n,
   double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

*n*<br/>
Bessel 函數的整數階數。

## <a name="return-value"></a>傳回值

這些常式都會傳回的 Bessel 函數*x*。 如果*x*中為負數 **_y0**， **_y1**，或 **_yn**函式，此常式會將**errno** 至**EDOM**，列印 **_DOMAIN**錯誤訊息， **stderr**，並傳回 **_HUGE_VAL**。 您可以修改錯誤處理使用 **_matherr**。

## <a name="remarks"></a>備註

**_J0**， **_j1**，和 **_jn**常式傳回 Bessel 函式的第一類： 分別排序 0、 1 和 n。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|**無效**|**_DOMAIN**|

**_Y0**， **_y1**，和 **_yn**常式傳回 Bessel 函式的第二類： 分別排序 0、 1 和 n。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|**無效**|**_DOMAIN**|
|± 0|**ZERODIVIDE**|**_SING**|
|&#124;x&#124; < 0.0|**無效**|**_DOMAIN**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_j0**， **_j1**， **_jn**， **_y0**， **_y1**， **_yn**|\<cmath> (C++)、\<math.h> (C、C++)|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_bessel1.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.387;
   int n = 3, c;

   printf( "Bessel functions for x = %f:\n", x );
   printf( "   Kind   Order  Function     Result\n\n" );
   printf( "   First  0      _j0( x )     %f\n", _j0( x ) );
   printf( "   First  1      _j1( x )     %f\n", _j1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );
   printf( "   Second 0      _y0( x )     %f\n", _y0( x ) );
   printf( "   Second 1      _y1( x )     %f\n", _y1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );
}
```

```Output
Bessel functions for x = 2.387000:
   Kind   Order  Function     Result

   First  0      _j0( x )     0.009288
   First  1      _j1( x )     0.522941
   First  2      _jn( 2, x )  0.428870
   First  3      _jn( 3, x )  0.195734
   First  4      _jn( 4, x )  0.063131
   Second 0      _y0( x )     0.511681
   Second 1      _y1( x )     0.094374
   Second 2      _yn( 2, x )  -0.432608
   Second 3      _yn( 3, x )  -0.819314
   Second 4      _yn( 4, x )  -1.626833
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_matherr](matherr.md)<br/>
