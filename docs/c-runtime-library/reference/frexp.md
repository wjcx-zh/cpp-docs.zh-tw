---
title: frexp、frexpf、frexpl
ms.date: 4/2/2020
api_name:
- frexp
- _o_frexp
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: 79fe70341f0d6fef1dc7fe00f872456a11972876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345803"
---
# <a name="frexp-frexpf-frexpl"></a>frexp、frexpf、frexpl

取得浮點數的尾數和指數。

## <a name="syntax"></a>語法

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>參數

*X.*<br/>
浮點值。

*expptr*<br/>
預存整數指數的指標。

## <a name="return-value"></a>傳回值

**弗雷智浦**返回曼蒂薩。 如果*x*為 0,則對於曼蒂薩和指數,函數返回 0。 如果*expptr*為**NULL,** 則無效參數處理程式將呼叫[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設置到**EINVAL**並返回0。

## <a name="remarks"></a>備註

**frexp**函數會浮點值 *(x*) 分解為曼蒂薩 *(m*) 和指數 *(n),* 以便*m*的絕對值大於或等於*x* = 0.5 和小於 1.0,x *m* = 2<sup>*n*</sup>。 整數指數*n*存儲在*expptr*指向的位置。

C++允許重載,所以你可以調用**frexp**的重載。 在 C 程式中 **,frexp**始終採用**雙**和**int**指標,並傳回**一個雙**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**弗雷浦普斯**,**弗雷克斯普 ,****弗勒克普爾**|\<math.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
