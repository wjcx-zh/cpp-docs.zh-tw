---
title: nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
description: Nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf 和 nexttowardl 的 API 參考;這會傳回下一個可表示的浮點值。
ms.date: 9/1/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
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
ms.openlocfilehash: cdcfb1a1d0bf1523a0252d779dba603ce1814b14
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555822"
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

#define nextafter(X, Y) // Requires C11 or higher

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );

#define nexttoward(X, Y) // Requires C11 or higher

float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>參數

*X*\
起始的浮點值。

*Y*\
要前往的浮點值。

## <a name="return-value"></a>傳回值

傳回在*y*的方向*x*之後，傳回類型的下一個表示浮點值。 如果 *x* 和 *y* 相等，則函式會傳回 *y*，轉換成傳回型別，但不會觸發任何例外狀況。 如果 *x* 不等於 *y*，且結果為 denormal 或零，則會設定 **FE_UNDERFLOW** 和 **FE_INEXACT** 浮點數例外狀況狀態，並傳回正確的結果。 如果 *x* 或 *y* 是 NAN，則傳回值是其中一個輸入的 nan。 如果 *x* 是有限的，且結果在類型中是無限或無法表示，則會傳回正確簽署的無限大或 NAN、 **FE_OVERFLOW** 和 **FE_INEXACT** 的浮點例外狀況狀態已設定，而且 **errno** 設定為 **ERANGE**。

## <a name="remarks"></a>備註

**Nextafter**和**nexttoward**函式系列是相等的，但*y*的參數類型除外。 如果 *x* 和 *y* 相等，則傳回的值會 *轉換成* 傳回型別。

因為 c + + 允許多載，所以如果您包含， \<cmath> 您可以呼叫 **nextafter** 和 **nexttoward** 的多載來傳回 **`float`** 和 **`long double`** 類型。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **nextafter** 和 **nexttoward** 一律會傳回 **`double`** 。

如果您使用 \<tgmath.h> `nextafter()` 或 `nexttoward()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

**_Nextafter**和 **_nextafterf**函式都是 Microsoft 特定的。 只有在針對 x64 進行編譯時，才可使用 **_nextafterf** 函數。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭 (C)|必要的標頭 (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**、 **nextafterf**、 **nextafterl**、 **_nextafterf**、 **nexttoward**、 **nexttowardf**、 **nexttowardl**|\<math.h>|\<math.h> 或 \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> 或 \<cfloat>|
|**nextafter** 宏，  **nexttoward** 宏| \<tgmath.h> ||

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)\
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)
