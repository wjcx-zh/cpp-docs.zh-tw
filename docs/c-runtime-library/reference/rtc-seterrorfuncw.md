---
title: _RTC_SetErrorFuncW
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
ms.openlocfilehash: 0d45e5c857e917ca23b62482c64a06314565226e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948970"
---
# <a name="_rtc_seterrorfuncw"></a>_RTC_SetErrorFuncW

指定函式做為報告執行階段錯誤檢查 (RTC) 的處理常式。

## <a name="syntax"></a>語法

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>參數

*function*<br/>
函式的位址，會處理執行階段錯誤檢查。

## <a name="return-value"></a>傳回值

先前定義的錯誤函式;如果沒有先前定義的函數，則**為 Null** 。

## <a name="remarks"></a>備註

在新程式碼中，只使用 **_RTC_SetErrorFuncW**。 **_RTC_SetErrorFunc**只包含在程式庫中，以提供回溯相容性。

**_RTC_SetErrorFuncW**回呼只適用于其所連結的元件，但不會全域套用。

請確定您傳遞給 **_RTC_SetErrorFuncW**的位址是有效錯誤處理函式的位址。

如果使用[_RTC_SetErrorType](rtc-seterrortype.md)指派了-1 類型的錯誤，則不會呼叫錯誤處理函式。

您必須先呼叫任一個執行階段錯誤檢查初始化函式，才能呼叫此函式。 如需詳細資訊，請參閱 [Using Run-Time Checks Without the C Run-Time Library](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。

**_RTC_error_fnW** 的定義如下：

```cpp
typedef int (__cdecl * _RTC_error_fnW)(
    int errorType,
    const wchar_t * filename,
    int linenumber,
    const wchar_t * moduleName,
    const wchar_t * format,
    ... );
```

其中：

*errorType*<br/>
[_RTC_SetErrorType](rtc-seterrortype.md)所指定之錯誤的類型。

*filename*<br/>
發生失敗的來源檔案；若無偵錯資訊，即為 null。

*linenumber*<br/>
發生錯誤之 *檔案名稱* 中的行；若無偵錯資訊，即為 0。

*moduleName*<br/>
發生失敗之 DLL 或可執行檔的名稱。

*格式*<br/>
printf 樣式字串，可使用剩餘的參數顯示錯誤訊息。 VA_ARGLIST 的第一個引數是所發生的 RTC 錯誤號碼。

如需示範如何使用 **_RTC_error_fnW** 的範例，請參閱[自訂原生執行階段檢查](/visualstudio/debugger/native-run-time-checks-customization)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
