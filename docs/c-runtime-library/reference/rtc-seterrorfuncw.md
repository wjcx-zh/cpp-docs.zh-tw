---
title: _RTC_SetErrorFuncW | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf610316c504e61d56556a20797f55d2906bca27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406910"
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW

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

先前定義的錯誤函式。或**NULL**如果沒有先前定義的函式。

## <a name="remarks"></a>備註

在新的程式碼，請一律使用 **_RTC_SetErrorFuncW**。 **_RTC_SetErrorFunc**只包含回溯相容性文件庫中。

**_RTC_SetErrorFuncW**回呼只適用於其所連結，此元件，但不是會全域。

請確定您將傳遞至的位址 **_RTC_SetErrorFuncW**是有效的錯誤處理函式。

如果錯誤已被指派為-1 的類型使用[_RTC_SetErrorType](rtc-seterrortype.md)，則不會呼叫錯誤處理函式。

您必須先呼叫任一個執行階段錯誤檢查初始化函式，才能呼叫此函式。 如需詳細資訊，請參閱 [Using Run-Time Checks Without the C Run-Time Library](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)。

**_RTC_error_fnW** 的定義如下：

> **typedef int (__cdecl \*_RTC_error_fnW) (int** *errorType* **，const wchar_t \***  *filename* **，int***linenumber* **，const wchar_t \***  *moduleName* **，const wchar_t \*** *格式* **，...)。** 

其中：

*errorType*所指定的錯誤類型的[_RTC_SetErrorType](rtc-seterrortype.md)。

*檔名*原始程式檔失敗發生的位置或如果沒有偵錯資訊則為 null。

*linenumber*中的一行*filename*失敗發生的位置，或 0，如果不未提供任何偵錯資訊。

*moduleName* DLL 或可執行檔名稱由發生失敗。

*格式*printf 樣式字串，以顯示錯誤訊息，使用剩餘的參數。 VA_ARGLIST 的第一個引數是所發生的 RTC 錯誤號碼。

如需示範如何使用 **_RTC_error_fnW** 的範例，請參閱[自訂原生執行階段檢查](/visualstudio/debugger/native-run-time-checks-customization)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)<br/>
