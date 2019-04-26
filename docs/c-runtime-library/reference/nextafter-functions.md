---
title: nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
ms.date: 04/05/2018
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: 0e0a60dc9f7c068d8c18c10f3c6b819b9e06d3b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156183"
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl

傳回下一個所能顯示的浮點值。

## <a name="syntax"></a>語法

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>參數

*x*<br/>
起始的浮點值。

*y*<br/>
要前往的浮點值。

## <a name="return-value"></a>傳回值

傳回下一步 可顯示的浮點值之後，傳回類型*x*方向*y*。 如果*x*並*y*相等，則函數會傳回*y*，轉換成傳回型別，以觸發任何例外狀況。 如果*x*不等於*y*，且結果為異常或零**FE_UNDERFLOW**並**FE_INEXACT**浮點例外狀況狀態已設定，並傳回正確的結果。 如果有任一*x*或是*y*是 NAN，則傳回的值是其中一個輸入 Nan。 如果*x*是有限的結果為無限或無法在類型中，正確簽署的無限大或 NAN 則會傳回，則**FE_OVERFLOW**並**FE_INEXACT**設定浮點例外狀況狀態，並**errno**設為**ERANGE**。

## <a name="remarks"></a>備註

**Nextafter**並**nexttoward**函式系列是相等的除了的參數型別*y*。 如果*x*並*y*相等，傳回的值是*y*轉換成傳回型別。

因為C++允許多載，如果您包含\<cmath> > 您可以呼叫多載**nextafter**並**nexttoward**傳回**float**和**長** **double**型別。 在 C 程式中， **nextafter**並**nexttoward**一律會傳回**double**。

**_Nextafter**並 **_nextafterf**函式是 Microsoft 專有的。 **_Nextafterf**函式只適用於 x64 編譯時。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**， **nextafterf**， **nextafterl**， **_nextafterf**， **nexttoward**， **nexttowardf**， **nexttowardl**|\<math.h>|\<math.h> 或 \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> 或 \<cfloat>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
