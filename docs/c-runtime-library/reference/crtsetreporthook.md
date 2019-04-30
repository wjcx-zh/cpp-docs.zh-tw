---
title: _CrtSetReportHook
ms.date: 11/04/2016
apiname:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 7dcb916ea920751618ffa6a4afbcde8df5e35cba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343039"
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

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

**_CrtSetReportHook**可讓應用程式到 C 執行階段偵錯程式庫報告處理序中使用它自己的報告函式。 因此，每當呼叫 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) 產生偵錯報告時，都會先呼叫應用程式的報告函式。 這項功能可讓應用程式執行作業，例如篩選偵錯報表，讓它可以專注於特定配置類型，或使用將報表傳送至目的地無法使用 **_CrtDbgReport**。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtSetReportHook**會在前置處理期間移除。

如需更強固的版本 **_CrtSetReportHook**，請參閱[_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md)。

**_CrtSetReportHook**函式會安裝新用戶端定義報告函式中指定*reportHook* ，並傳回先前的用戶端定義攔截程序。 下列範例示範用戶端定義的報表攔截程序應如何設計原型：

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

何處*reportType*是偵錯報告類型 (**_CRT_WARN**， **_CRT_ERROR**，或 **_CRT_ASSERT**)，*訊息*是完全組裝的偵錯使用者訊息，而無法容納在報表中，並**returnValue**指定用戶端定義的值會報告應該傳回的函式 **_CrtDbgReport**。 如需可用報表類型的完整說明，請參閱 [_CrtSetReportMode](crtsetreportmode.md) 函式。

如果用戶端定義報告函式完全處理偵錯訊息，使得任何進一步的回報是必要功能，則此函式應傳回 **，則為 TRUE**。 當函式會傳回**假**， **_CrtDbgReport**呼叫來產生偵錯報表的報表類型、 模式和檔案中使用目前的設定。 此外，藉由指定 **_CrtDbgReport**傳回值中的**returnValue**，應用程式也可以控制是否會發生偵錯中斷。 如何設定及產生偵錯報表的完整描述，請參閱 < **_CrtSetReportMode**， [_CrtSetReportFile](crtsetreportfile.md)，並 **_CrtDbgReport**。

如需使用支援攔截程序之其他執行階段函式，以及撰寫您自己的用戶端定義攔截函式的詳細資訊，請參閱[撰寫偵錯攔截函式](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> 如果您的應用程式會使用編譯 **/clr**和報告的函式之後呼叫應用程式結束 main，CLR 將會擲回例外狀況，如果報告的函式呼叫任何 CRT 函式。

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
