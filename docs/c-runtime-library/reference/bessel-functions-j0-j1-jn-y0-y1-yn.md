---
title: Bessel 函數：_j0、_j1、_jn、_y0、_y1、_yn
ms.date: 04/05/2018
api_name:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
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
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
ms.openlocfilehash: 5420b34846998cdbcb4814d8319274f1a3516d91
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939465"
---
# <a name="bessel-functions-_j0-_j1-_jn-_y0-_y1-_yn"></a>Bessel 函數：_j0、_j1、_jn、_y0、_y1、_yn

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

這些常式都會傳回*x*的貝賽耳函數。 如果 **_y0**、 **_y1**或 **_yn**函式中的*x*是負數，常式會將**errno**設定為**EDOM**、將 **_DOMAIN**錯誤訊息列印到**stderr**，然後傳回 **_HUGE_VAL**。 您可以使用 **_matherr**來修改錯誤處理。

## <a name="remarks"></a>備註

**_J0**、 **_j1**和 **_jn**常式會分別傳回第一種的貝賽耳函式：訂單0、1和 n。

|Input|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|**無效**|**_DOMAIN**|

**_Y0**、 **_y1**和 **_yn**常式會傳回第二種類型的貝賽耳函式：分別是訂單0、1和 n。

|Input|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± **QNAN**， **IND**|**無效**|**_DOMAIN**|
|± 0|**ZERODIVIDE**|**_SING**|
|&#124;x&#124; < 0。0|**無效**|**_DOMAIN**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_j0**、 **_j1**、 **_jn**、 **_y0**、 **_y1**、 **_yn**|\<cmath> (C++)、\<math.h> (C、C++)|

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
