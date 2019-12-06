---
title: nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
ms.date: 04/05/2018
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
ms.openlocfilehash: c6b100fb24d879a16780650d8a374ec26f28c048
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857719"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl

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

以*y*的方向傳回*x*之後，傳回類型的下一個顯示浮點值。 如果*x*和*y*相等，函式會傳回*y*，轉換成傳回型別，而不會觸發例外狀況。 如果*x*不等於*y*，且結果為 denormal 或零，則會設定**FE_UNDERFLOW**和**FE_INEXACT**浮點例外狀況狀態，並傳回正確的結果。 如果*x*或*y*是 NAN，則傳回值是其中一個輸入 nan。 如果*x*是有限的，且結果在類型中為無限或無法顯示，則會傳回正確的無限大或 NAN，並設定**FE_OVERFLOW**和**FE_INEXACT**浮點例外狀況狀態，而且**errno**會設定為**ERANGE**。

## <a name="remarks"></a>備註

除了*y*的參數類型之外， **nextafter**和**nexttoward**函數系列是相等的。 如果*x*和*y*相等，則傳回的值會*轉換為*傳回型別。

因為C++允許多載，所以如果您包含 \<h > 您可以呼叫傳回**float**和**long** **double**類型的**nextafter**和**nexttoward**的多載。 在 C 程式中， **nextafter**和**nexttoward**一律會傳回**double**。

**_Nextafter**和 **_nextafterf**函式為 Microsoft 特有的功能。 只有在針對 x64 進行編譯時，才能使用 **_nextafterf**函數。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**、 **nextafterf**、 **nextafterl**、 **_nextafterf**、 **nexttoward**、 **nexttowardf**、 **nexttowardl**|\<math.h>|\<math.h> 或 \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> 或 \<cfloat>|

如需相容性的詳細資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
