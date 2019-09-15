---
title: hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl
ms.date: 04/05/2018
api_name:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
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
- hypotf
- hypotl
- _hypotl
- hypot
- _hypot
- _hypotf
helpviewer_keywords:
- hypotenuse calculation
- hypot function
- hypotf function
- triangles, calculating hypotenuse
- hypotl function
- calculating hypotenuses
- _hypot function
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
ms.openlocfilehash: 8cee9e217b23c43a9ce5a1521b52215301b932fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954784"
---
# <a name="hypot-hypotf-hypotl-_hypot-_hypotf-_hypotl"></a>hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl

計算斜邊。

## <a name="syntax"></a>語法

```C
double hypot(
   double x,
   double y
);
float hypotf(
   float x,
   float y
);
long double hypotl(
   long double x,
   long double y
);
double _hypot(
   double x,
   double y
);
float _hypotf(
   float x,
   float y
);
long double _hypotl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>參數

*x*、 *y*<br/>
浮點值。

## <a name="return-value"></a>傳回值

如果成功， **hypot**會傳回斜邊的長度;溢位時， **hypot**會傳回 INF （無限大），而**errno**變數會設定為**ERANGE**。 您可以使用 **_matherr**來修改錯誤處理。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Hypot**函數會計算直角三角形的斜邊長度，指定兩端*x*和*y*的長度（換言之， *x*<sup>2</sup>  +  *y*<sup>2</sup>的平方根）。

具有前置底線的函式版本提供舊版標準的相容性。 其行為與不具有前置底線的版本完全相同。 建議針對新程式碼使用不具有前置底線的版本。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**hypot**、 **hypotf**、 **hypotl**、 **_hypot**、 **_hypotf**、 **_hypotl**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_hypot.c
// This program prints the hypotenuse of a right triangle.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 3.0, y = 4.0;

   printf( "If a right triangle has sides %2.1f and %2.1f, "
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );
}
```

```Output
If a right triangle has sides 3.0 and 4.0, its hypotenuse is 5.0
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[_matherr](matherr.md)<br/>