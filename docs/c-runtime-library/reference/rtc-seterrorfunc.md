---
title: _RTC_SetErrorFunc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_SetErrorFunc
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
apitype: DLLExport
f1_keywords:
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
dev_langs:
- C++
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e146f699f9026260470b1c540c7567f074896a38
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451611"
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

指定函式做為報告執行階段錯誤檢查 (RTC) 的處理常式。 此函式已被取代。使用 **_RTC_SetErrorFuncW**改為。

## <a name="syntax"></a>語法

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>參數

*function*<br/>
函式的位址，會處理執行階段錯誤檢查。

## <a name="return-value"></a>傳回值

先前所定義的錯誤函式。 如果沒有先前定義的函式，會傳回**NULL**。

## <a name="remarks"></a>備註

請勿使用此函式。請改用 **_RTC_SetErrorFuncW**。 保留此函式的目的只在提供回溯相容性。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
