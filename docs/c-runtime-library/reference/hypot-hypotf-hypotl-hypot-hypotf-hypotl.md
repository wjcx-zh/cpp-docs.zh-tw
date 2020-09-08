---
title: hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl
description: Hypot、hypotf、hypotl、_hypot、_hypotf 和 _hypotl 的 API 參考;計算斜邊的。
ms.date: 9/1/2020
api_name:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
- _o__hypot
- _o__hypotf
- _o_hypot
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 199e330dcd78c372a0279cac9f0e96cb47c561e8
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556446"
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
#define hypotf(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*x*、 *y*\
浮點值。

## <a name="return-value"></a>傳回值

如果成功， **hypot** 會傳回斜邊的長度;溢位時， **hypot** 會將 INF (無限大) ，而且 **errno** 變數會設定為 **ERANGE**。 您可以使用 **_matherr** 修改錯誤處理。

如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Hypot**函式會計算直角三角形的斜邊長度，指定兩側*x*和*y*的長度 (換句話說，也就是*x*<sup>2</sup>  +  *y*<sup>2</sup>) 的平方根。

具有前置底線的函式版本提供舊版標準的相容性。 其行為與不具有前置底線的版本完全相同。 建議針對新程式碼使用不具有前置底線的版本。

如果您使用 \<tgmath.h> `hypot()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**hypot**、 **hypotf**、 **hypotl**、 **_hypot**、 **_hypotf** **_hypotl**|\<math.h>|
|**hypot** 宏 | \<tgmath.h> |

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
