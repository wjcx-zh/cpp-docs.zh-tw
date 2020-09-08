---
title: _chgsign、_chgsignf、_chgsignl
description: _Chgsign、_chgsignf 和 _chgsignl 的 API 參考;這會反轉浮點數引數的正負號。
ms.date: 04/05/2018
api_name:
- _chgsignl
- _chgsign
- _chgsignf
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
- _chgsignf
- chgsign
- _chgsignl
- _chgsign
helpviewer_keywords:
- _chgsignl function
- _chgsignf function
- chgsign function
- _chgsign function
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
ms.openlocfilehash: 7dc934f3c2d22cc36abe5f31f7d64e0674ccdd3a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555198"
---
# <a name="_chgsign-_chgsignf-_chgsignl"></a>_chgsign、_chgsignf、_chgsignl

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

**_Chgsign**函式會傳回等於浮點數引數*x*的值，但其正負號反轉。 不會傳回錯誤。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_chgsign**|\<float.h>|
|**_chgsignf**， **_chgsignl**|\<math.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)<br/>
