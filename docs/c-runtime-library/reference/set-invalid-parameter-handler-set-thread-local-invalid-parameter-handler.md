---
title: _set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler
description: _Set_invalid_parameter_handler 和 _set_thread_local_invalid_parameter_handler 的 API 參考;這會設定當 CRT 偵測到不正確引數時，所要呼叫的函式。
ms.date: 4/2/2020
api_name:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
- _o__set_invalid_parameter_handler
- _o__set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: a965bd71af18a57c31d3cfef927be02005c407c0
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555614"
---
# <a name="_set_invalid_parameter_handler-_set_thread_local_invalid_parameter_handler"></a>_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler

設定要在 CRT 偵測到無效引數時呼叫的函式。

## <a name="syntax"></a>語法

```C
_invalid_parameter_handler _set_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
```

### <a name="parameters"></a>參數

*pNew*<br/>
新無效的參數處理常式的函式指標。

## <a name="return-value"></a>傳回值

呼叫前的無效的參數處理常式的指標。

## <a name="remarks"></a>備註

許多 C 執行階段函式都會檢查傳遞給它們之引數的有效性。 如果傳遞了不正確引數，函式可以設定 **errno** 錯誤號碼或傳回錯誤碼。 在這種情況下，也會呼叫無效的參數處理常式。 C 執行階段會提供預設全域無效的參數處理常式，以終止程式，並顯示執行階段錯誤訊息。 您可以使用 **_set_invalid_parameter_handler** 將您自己的函式設定為全域不正確參數處理常式。 C 執行階段也支援執行緒區域無效的參數處理常式。 如果線上程中使用 **_set_thread_local_invalid_parameter_handler**設定執行緒區域參數處理常式，則從執行緒呼叫的 C 執行時間函式會使用該處理常式，而不是使用全域處理常式。 一次只有一個函式可以指定為全域無效引數處理常式。 只有一個函式可以指定為一個執行緒的執行緒區域無效引數處理常式，但不同的執行緒可以有不同的執行緒區域處理常式。 這可讓您變更程式碼某個部分所用的處理常式，而不會影響其他執行緒的行為。

執行階段呼叫無效參數函式時，通常表示發生無法復原的錯誤。 您提供的無效的參數處理常式函式應該會在儲存後中止任何資料。 除非您確信錯誤可復原，否則它不應該將控制權傳回給 main 函數。

無效的參數處理常式函式必須具有下列原型︰

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

*運算式*引數是引發錯誤之引數運算式的寬字元串表示。 *函數*引數是收到無效引數的 CRT 函數名稱。 *File*引數是包含函式之 CRT 原始程式檔的名稱。 *Line*引數是該檔案中的行號。 最後一個引數會予以保留。 除非使用 CRT 程式庫的 debug 版本，否則所有參數都具有 **Null** 值。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_invalid_parameter_handler**， **_set_thread_local_invalid_parameter_handler**|C： \<stdlib.h><br /><br /> C + +： \<cstdlib> 或 \<stdlib.h>|

**_Set_invalid_parameter_handler**和 **_set_thread_local_invalid_parameter_handler**函式都是 Microsoft 特定的。 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

在下列範例中，無效的參數錯誤處理常式是用來列印收到無效參數以及 CRT 來源中檔案和行的函式。 使用偵錯 CRT 程式庫時，無效參數錯誤也會引發判斷提示，而在這個範例中使用 [_CrtSetReportMode](crtsetreportmode.md) 予以停用。

```C
// crt_set_invalid_parameter_handler.c
// compile with: /Zi /MTd
#include <stdio.h>
#include <stdlib.h>
#include <crtdbg.h>  // For _CrtSetReportMode

void myInvalidParameterHandler(const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter detected in function %s."
            L" File: %s Line: %d\n", function, file, line);
   wprintf(L"Expression: %s\n", expression);
   abort();
}

int main( )
{
   char* formatString;

   _invalid_parameter_handler oldHandler, newHandler;
   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);

   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   // Call printf_s with invalid parameters.

   formatString = NULL;
   printf(formatString);
}
```

```Output
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32
Expression: format != nullptr
```

## <a name="see-also"></a>另請參閱

[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[CRT 函式的安全性增強版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
