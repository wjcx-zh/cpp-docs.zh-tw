---
title: _chgsign、_chgsignf、_chgsignl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _chgsignl
- _chgsign
- _chgsignf
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
- _chgsignf
- chgsign
- _chgsignl
- _chgsign
dev_langs:
- C++
helpviewer_keywords:
- _chgsignl function
- _chgsignf function
- chgsign function
- _chgsign function
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 781359972b67b2634f8f762fac98bf9216ef5ab5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393439"
---
# <a name="chgsign-chgsignf-chgsignl"></a>_chgsign、_chgsignf、_chgsignl

變換浮點引數的正負號。

## <a name="syntax"></a>語法

```C
double _chgsign(
   double x
);
float _chgsignf(
   float x
);
long double _chgsignl(
   long double x
);
```

### <a name="parameters"></a>參數

*x*<br/>
要變更的浮點值。

## <a name="return-value"></a>傳回值

**_Chgsign**函式會傳回等於浮點引數的值*x*，但正負號相反。 不會傳回錯誤。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_chgsign**|\<float.h>|
|**_chgsignf**， **_chgsignl**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)<br/>
