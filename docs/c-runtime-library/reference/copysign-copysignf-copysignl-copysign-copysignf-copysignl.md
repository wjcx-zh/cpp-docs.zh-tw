---
title: copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
description: '適用于傳回值的 API 參考，其大小為一個引數，另一個使用 copysign 的正負號 ( # A1'
ms.date: 9/1/2020
api_name:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 8f9ffe56e82f6a82da15fde3f8efea60fc1c0f9f
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554860"
---
# <a name="copysign-copysignf-copysignl-_copysign-_copysignf-_copysignl"></a>copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl

傳回一個值，具有其中一個引數的大小和另一個引數的正負號。

## <a name="syntax"></a>語法

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
#define copysign(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
傳回為結果大小的浮點值。

*Y*\
傳回為結果正負號的浮點值。

[浮點支援常式](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>傳回值

**Copysign**函式會傳回浮點值，此值會結合*x*的大小和*y*的正負號。 不會傳回錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回或值的 **copysign** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **copysign** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `copysign()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign**、 **copysignf**、 **copysignl**、 **_copysignf**、 **_copysignl**|\<math.h>|
|**copysign** 宏 | \<tgmath.h> |

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign、_chgsignf、_chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
