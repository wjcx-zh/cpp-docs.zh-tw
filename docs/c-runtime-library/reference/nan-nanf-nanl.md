---
title: nan、nanf、nanl | Microsoft Docs
ms.custom: ''
ms.date: 94/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- nanf
- nan
- nanl
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
- nan
- nanl
- nanf
dev_langs:
- C++
helpviewer_keywords:
- nan function
- nanf function
- nanl function
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2fa378cdded71f0f99ad0fbe152d1282c9e6fe4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="nan-nanf-nanl"></a>nan、nanf、nanl

傳回無訊息 NaN 值。

## <a name="syntax"></a>語法

```C
double nan( const char* input );
float nanf( const char* input );
long double nanl( const char* input );
```

### <a name="parameters"></a>參數

*input*<br/>
字串值。

## <a name="return-value"></a>傳回值

**Nan**函式會傳回無訊息 NaN 值。

## <a name="remarks"></a>備註

**Nan**函式會傳回無訊息 （非發出訊號） NaN 值對應的浮點值。 *輸入*值會被忽略。 如需 NAN 如何在輸出中表示的資訊，請參閱 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**nan**， **nanf**， **nanl**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[_finite、_finitef](finite-finitef.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
