---
title: remquo、remquof、remquol
ms.date: 04/05/2018
api_name:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: c96357dda007e9bf12ddaf6091af47794bfc0630
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949368"
---
# <a name="remquo-remquof-remquol"></a>remquo、remquof、remquol

計算兩個整數值的餘數，並且將帶有正負號和商數近似大小的整數值儲存在參數中指定的位置。

## <a name="syntax"></a>語法

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
```

```cpp
float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>參數

*推*<br/>
分子。

*denom*<br/>
分母。

*現狀*<br/>
用來儲存具有正負號和商數近似大小的整數的指標。

## <a name="return-value"></a>傳回值

**remquo**會傳回*x*  /  *y*的浮點餘數。 如果*y*的值是0.0，則**remquo**會傳回無訊息 NaN。 如需**printf**系列表示無訊息 NaN 的資訊，請參閱[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**Remquo**函數會計算*x*  /  *y*的浮點餘數*f* ，例如*x*  =  *i* \* *y*  +  *f*，其中*i*是一個整數， *f*具有與*x*相同的正負號，而*f*的絕對值小於*y*的絕對值。

C++允許多載，因此您可以呼叫採用並傳回**浮點數**或**長** **雙精度**值之**remquo**的多載。 在 C 程式中， **remquo**一律採用兩個**雙**精確度引數，並傳回**雙精度浮點數**。

## <a name="requirements"></a>需求

|函數|必要的標頭 (C)|必要的標頭 (C++)|
|--------------|---------------------|-|
|**remquo**、 **remquof**、 **remquol**|\<math.h>|\<cmath> 或 \<math.h>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
