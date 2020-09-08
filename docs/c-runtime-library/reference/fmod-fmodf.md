---
title: fmod、fmodf、fmodl
description: Fmod、fmodf 和 fmodl 的 API 參考;計算浮點餘數的。
ms.date: 9/1/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 2b610dec79c98b973af09f8efb147ad6797f7946
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556082"
---
# <a name="fmod-fmodf-fmodl"></a>fmod、fmodf、fmodl

計算浮點餘數。

## <a name="syntax"></a>語法

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);

#define fmod(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*x*、 *y*\
浮點值。

## <a name="return-value"></a>傳回值

**fmod**會傳回*x*  /  *y*的浮點餘數。 如果 *y* 的值為0.0， **fmod** 會傳回無訊息 NaN。 如需 **printf** 系列表示無訊息 NaN 的詳細資訊，請參閱 [printf](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>備註

**Fmod**函式會計算*x*y 的浮點餘數*f*  /  *y* ，例如*x*  =  *i* \* *y*  +  *f*，其中*i*是整數， *f*的正負號等於*x*， *f*的絕對值小於*y*的絕對值。

C + + 允許多載，所以您可以呼叫採用和傳回值的 **fmod** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **fmod** 一律會採用兩個 **`double`** 引數，並傳回 **`double`** 。

如果您使用 \<tgmath.h> `fmod()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|函式|必要的標頭|
|--------------|---------------------|
|**fmod**、 **fmodf**、 **fmodl**|\<math.h>|
|**fmod** 宏 | \<tgmath.h> |

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
