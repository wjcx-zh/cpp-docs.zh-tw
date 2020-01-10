---
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 77c1e499c66a76027e872783e256754ef72e465d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938518"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

將用戶端定義的報告函式連結到 C 執行階段偵錯報告處理序，以進行安裝 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>參數

*reportHook*<br/>
要連結到 C 執行階段偵錯報告處理序的新用戶端定義報告函式。

## <a name="return-value"></a>傳回值

傳回上一個用戶端定義的報告函式。

## <a name="remarks"></a>備註

**_CrtSetReportHook**可讓應用程式將自己的報告函式用於 C 執行時間的 debug 程式庫報告進程。 因此，每當呼叫 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) 產生偵錯報告時，都會先呼叫應用程式的報告函式。 這項功能可讓應用程式執行一些作業，例如篩選「偵錯工具」報告，讓它可以專注于特定的配置類型，或將報表傳送至無法使用 **_CrtDbgReport**取得的目的地。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtSetReportHook**的呼叫。

如需更穩固的 **_CrtSetReportHook**版本，請參閱[_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md)。

**_CrtSetReportHook**函數會安裝*reportHook*中指定的新用戶端定義報告函式，並傳回先前的用戶端定義攔截。 下列範例示範用戶端定義的報表攔截程序應如何設計原型：

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

其中*reportType*是 debug 報表類型（ **_CRT_WARN**、 **_CRT_ERROR**或 **_CRT_ASSERT**），*訊息*是要包含在報表中的完整組合的 debug 使用者訊息，而**returnValue**是值由用戶端定義的報告函式指定，此函數應由 **_CrtDbgReport**傳回。 如需可用報表類型的完整說明，請參閱 [_CrtSetReportMode](crtsetreportmode.md) 函式。

如果用戶端定義的報告函式完全處理 debug 訊息，而不需要進一步的報告，則函式應該會傳回**TRUE**。 當函式傳回**FALSE**時，會呼叫 **_CrtDbgReport** ，以使用報表類型、模式和檔案的目前設定來產生「偵錯工具」報表。 此外，藉由在**returnValue**中指定 **_CrtDbgReport**傳回值，應用程式也可以控制是否發生「偵測中斷」。 如需如何設定和產生偵錯工具的完整說明，請參閱 **_CrtSetReportMode**、 [_CrtSetReportFile](crtsetreportfile.md)和 **_CrtDbgReport**。

如需使用支援攔截程序之其他執行階段函式，以及撰寫您自己的用戶端定義攔截函式的詳細資訊，請參閱[撰寫偵錯攔截函式](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> 如果您的應用程式是使用 **/clr**編譯的，而且在應用程式結束 main 之後呼叫報告函式，則 clr 會在報告函數呼叫任何 CRT 函數時擲回例外狀況（exception）。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
