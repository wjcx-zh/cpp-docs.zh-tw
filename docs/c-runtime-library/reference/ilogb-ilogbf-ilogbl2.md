---
title: ilogb、ilogbf、ilogbl2
description: Ilogb、ilogbf 和 ilogbl2 的 API 參考;它會取出整數，代表指定值的非偏誤基底2指數。
ms.date: 9/1/2020
api_name:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
ms.openlocfilehash: b27c329cca1edb9d30bb6b9b641f94d174c9c406
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556368"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb、ilogbf、ilogbl

擷取代表指定值之非偏誤基底 2 指數的整數。

## <a name="syntax"></a>語法

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);

#define ilogbl(X) // Requires C11 or higher
```

### <a name="parameters"></a>參數

*X*\
指定值。

## <a name="return-value"></a>傳回值

如果成功，則傳回 *x* 的以2為底數的指數作為 **`signed int`** 值。

否則，會傳回下列定義的其中一個值 \<math.h> ：

|輸入|結果|
|-----------|------------|
|±0|FP_ILOGB0|
|± inf、± nan、不定|FP_ILOGBNAN|

依 [_matherr](matherr.md) 中的指定回報錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫採用和傳回和類型的 **ilogb** 多載 **`float`** **`long double`** 。 在 C 程式中，除非您要使用 \<tgmath.h> 宏來呼叫這個函式，否則 **ilogb** 一律會採用並傳回 **`double`** 。

如果您使用 \<tgmath.h> `ilogb()` 宏，則引數的類型會決定所選取的函式版本。 如需詳細資料，請參閱 [類型-泛型數學](../../c-runtime-library/tgmath.md) 。

呼叫此函式類似于呼叫相等的 **logb** 函式，然後將傳回值轉換為 **`int`** 。

## <a name="requirements"></a>規格需求

|常式傳回的值|C 標頭|C++ 標頭|
|-------------|--------------|------------------|
|**ilogb**、 **ilogbf**、 **ilogbl**|\<math.h>|\<cmath>|
|**ilogb** 宏 | \<tgmath.h> ||

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函數參考](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb、logbf、logbl、_logb、_logbf](logb-logbf-logbl-logb-logbf.md)<br/>
