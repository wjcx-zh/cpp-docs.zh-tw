---
title: remquo、remquof、remquol
description: Remquo、remquof 和 remquol 的 API 參考;這會計算兩個整數值的餘數，並將具有正負號和大約量值的整數值儲存在參數中所指定的位置。
ms.date: 9/1/2020
api_name:
- remquof
- remquo
- remquol
- _o_remquo
- _o_remquof
- _o_remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: d99204ad9a80c6320869cbb72aee905981a5224d
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554964"
---
# <a name="remquo-remquof-remquol"></a>remquo、remquof、remquol

計算兩個整數值的餘數，並且將帶有正負號和商數近似大小的整數值儲存在參數中指定的位置。

## <a name="syntax"></a>語法

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
#define remquo(X, Y, INT_PTR) // Requires C11 or higher

float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>參數

*推*\
分子。

*denom*\
分母。

*現狀*\
用來儲存具有正負號和商數近似大小的整數的指標。

## <a name="return-value"></a>傳回值

**remquo**會傳回*x*  /  *y*的浮點餘數。 如果 *y* 的值為0.0， **remquo** 會傳回無訊息 NaN。 如需 **printf** 系列表示無訊息 NaN 的詳細資訊，請參閱 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**Remquo**函式會計算*x*y 的浮點餘數*f*  /  *y* ，例如*x*  =  *i* \* *y*  +  *f*，其中*i*是整數， *f*的正負號等於*x*， *f*的絕對值小於*y*的絕對值。

C + + 允許多載，所以您可以呼叫採用和傳回或值的 **remquo** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **remquo** 一律會採用兩個 **`double`** 引數，並傳回 **`double`** 。

如果您使用 \<tgmath.h> `remquo()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------|-|
|**remquo**、 **remquof**、 **remquol**|\<math.h>|\<cmath> 或 \<math.h>|
|**remquo** 宏 | \<tgmath.h> ||

如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[remainder、remainderf、remainderl](remainder-remainderf-remainderl.md)<br/>
