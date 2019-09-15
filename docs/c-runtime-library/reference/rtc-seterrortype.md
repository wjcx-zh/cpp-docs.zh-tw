---
title: _RTC_SetErrorType
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorType
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- RTC_SetErrorType
- _RTC_SetErrorType
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 6c1eff5920931aa3b72bf3dbc6232c371828b16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948928"
---
# <a name="_rtc_seterrortype"></a>_RTC_SetErrorType

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
值，會指派給此 *errnum*。 例如，您可以使用 **_CRT_ERROR**。 如果您使用 **_CrtDbgReport**做為錯誤處理常式， *ErrType*只能是[_CrtSetReportMode](crtsetreportmode.md)中所定義的其中一個符號。 若您有自己的錯誤處理常式 ([_RTC_SetErrorFunc](rtc-seterrorfunc.md))，您可以有可以有和 *errnum*等量的 *ErrType*。

_RTC_ERRTYPE_IGNORE 的*ErrType*對 **_CrtSetReportMode**具有特殊意義;此錯誤會被忽略。

## <a name="return-value"></a>傳回值

錯誤類型*類型*的先前值。

## <a name="remarks"></a>備註

所有錯誤的預設設定皆為 *ErrType* = 1，與 **_CRT_ERROR**相對應。 如需預設錯誤類型 (例如 **_CRT_ERROR**) 的詳細資訊，請參閱 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md)。

您必須先呼叫任一個執行階段錯誤檢查初始化函式，才能呼叫此函式。請參閱[不使用 C 語言執行階段程式庫進行執行階段檢查](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
