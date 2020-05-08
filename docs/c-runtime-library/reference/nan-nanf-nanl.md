---
title: nan、nanf、nanl
ms.date: 4/2/2020
api_name:
- nanf
- nan
- nanl
- _o_nan
- _o_nanf
- _o_nanl
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
- nan
- nanl
- nanf
helpviewer_keywords:
- nan function
- nanf function
- nanl function
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
ms.openlocfilehash: 77e933b971312097ec9eddd342b3b4dc2df34204
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914592"
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

**Nan**函數會傳回無訊息 nan 值。

## <a name="remarks"></a>備註

**Nan**函數會傳回對應于無訊息（非信號） nan 的浮點值。 *輸入*值會被忽略。 如需 NAN 如何在輸出中表示的資訊，請參閱 [printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**nan**、 **nanf**、 **nanl**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
