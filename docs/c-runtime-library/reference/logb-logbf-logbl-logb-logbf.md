---
title: logb、logbf、logbl、_logb、_logbf
ms.date: 04/05/2018
api_name:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
ms.openlocfilehash: c5fc59f786b00dcf4ab1056424d8442a03f3adbf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953157"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>logb、logbf、logbl、_logb、_logbf

擷取浮點引數的指數值。

## <a name="syntax"></a>語法

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>參數

*x*<br/>
浮點值。

## <a name="return-value"></a>傳回值

**logb**會以浮點值表示的帶正負號整數，傳回*x*的非偏誤指數值。

## <a name="remarks"></a>備註

**Logb**函式會將浮點引數*x*的指數值解壓縮，如同*x*是以無限範圍表示。 如果引數*x*反正規化，則會將它視為正規化。

因為C++允許多載，所以您可以呼叫採用並傳回**float**或**long** **double**值之**logb**的多載。 在 C 程式中， **logb**一律會採用並傳回**雙精度浮點數**。

|Input|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± QNAN，IND|無|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_logb**|\<float.h>|
|**logb**、 **logbf**、 **logbl**、 **_logbf**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
