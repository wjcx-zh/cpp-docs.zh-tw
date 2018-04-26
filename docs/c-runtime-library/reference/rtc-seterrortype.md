---
title: _RTC_SetErrorType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9fcca983247f0f5e0c09899e7ebec2774ca92e6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType

關聯的執行階段錯誤檢查 (RTC) 所偵測到的錯誤與類型。 錯誤處理常式會處理如何輸出指定類型的錯誤。

## <a name="syntax"></a>語法

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>參數

*errnum*<br/>
數字，介於零與 [_RTC_NumErrors](rtc-numerrors.md) 所傳回的值減一之間。

*ErrType*<br/>
值，會指派給此 *errnum*。 例如，您可以使用 **_CRT_ERROR**。 如果您使用 **_CrtDbgReport**錯誤處理常式中，為*ErrType*只能一個中定義的符號[_CrtSetReportMode](crtsetreportmode.md)。 如果您有自己的錯誤處理常式 ([_RTC_SetErrorFunc](rtc-seterrorfunc.md))，則可以有數目與 *errnum*相同的 *ErrType*。

*ErrType* _RTC_ERRTYPE_IGNORE 具有特殊意義 **_CrtSetReportMode**; 已忽略錯誤。

## <a name="return-value"></a>傳回值

先前的錯誤類型值*類型*。

## <a name="remarks"></a>備註

所有錯誤的預設設定皆為 *ErrType* = 1，與 **_CRT_ERROR**相對應。 如需預設錯誤類型 (例如 **_CRT_ERROR**) 的詳細資訊，請參閱 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md)。

您必須先呼叫任一個執行階段錯誤檢查初始化函式，才能呼叫此函式。請參閱[不使用 C 語言執行階段程式庫進行執行階段檢查](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
