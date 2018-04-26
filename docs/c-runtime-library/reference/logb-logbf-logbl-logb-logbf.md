---
title: logb、logbf、logbl、_logb、_logbf | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
dev_langs:
- C++
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f279d2b31ba9a40dd3d5c0e5d3c50e5a9a4b170
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb、logbf、logbl、_logb、_logbf

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

**logb**傳回非偏誤指數值*x*為帶正負號整數，表示為浮點數的值。

## <a name="remarks"></a>備註

**Logb**函式會擷取浮點引數的指數值*x*，如同*x*表示無限的範圍。 如果引數*x*為未標準化，它會被視為已正規化。

因為 c + + 允許多載，所以您可以呼叫的多載**logb**採用並傳回**float**或**長** **double**值。 在 C 程式中， **logb**一律採用並傳回**double**。

|輸入|SEH 例外狀況|Matherr 例外狀況|
|-----------|-------------------|-----------------------|
|± QNAN、IND|無|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_logb**|\<float.h>|
|**logb**， **logbf**， **logbl**， **_logbf**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
