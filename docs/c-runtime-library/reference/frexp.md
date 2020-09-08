---
title: frexp、frexpf、frexpl
description: Frexp、frexpf 和 frexpl 的 API 參考;，可取得浮點數的尾數和指數。
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a23de4160abcfab2518125bfa0fd35a389901674
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555744"
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
#define frexpl(X, INT_PTR) // Requires C11 or higher
```

```cpp
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

*X*\
浮點值。

*expptr*\
預存整數指數的指標。

## <a name="return-value"></a>傳回值

**frexp** 會傳回尾數。 如果 *x* 是0，則函數會針對尾數和指數傳回0。 如果 *expptr* 為 **Null**，則會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將 **errno** 設定為 **EINVAL** ，並傳回0。

## <a name="remarks"></a>備註

**Frexp**函式會將浮點值 (*x*) 細分為尾數 (*m*) 和指數 (*n*) ，使*m*的絕對值大於或等於0.5 且小於1.0，以及*x*  =  *m* * 2<sup>*n*</sup>。 整數指數 *n* 會儲存在 *expptr*所指向的位置。

C + + 允許多載，所以您可以呼叫 **frexp**的多載。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **frexp** 一律會採用 **`double`** 和 **`int`** 指標，並傳回 **`double`** 。

如果您使用 \<tgmath.h> `frexp()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的標頭|
|--------------|---------------------|
|**frexp**、 **frexpf**、 **frexpl**|\<math.h>|
|**frexp** 宏 | \<tgmath.h> |

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
