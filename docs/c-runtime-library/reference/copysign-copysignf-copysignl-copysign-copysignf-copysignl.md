---
title: copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
apilocation:
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
apitype: DLLExport
f1_keywords:
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
dev_langs:
- C++
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f54b45e0b4488e76c501f67b1e98de071157ad7f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394726"
---
# <a name="copysign-copysignf-copysignl-copysign-copysignf-copysignl"></a>copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl

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
```

### <a name="parameters"></a>參數

*x*<br/>
傳回為結果大小的浮點值。

*y*<br/>
傳回為結果正負號的浮點值。

[浮點支援常式](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>傳回值

**Copysign**函式會傳回浮點值，結合的量級*x*和簽章的*y*。 不會傳回錯誤。

## <a name="remarks"></a>備註

因為 c + + 允許多載，所以您可以呼叫的多載**copysign**採用並傳回**float**或**長** **double**值。 在 C 程式中， **copysign**一律採用並傳回**double**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign**， **copysignf**， **copysignl**， **_copysignf**， **_copysignl**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign、_chgsignf、_chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
