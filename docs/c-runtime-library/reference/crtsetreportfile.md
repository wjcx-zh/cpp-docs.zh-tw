---
title: _CrtSetReportFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3df4f54ad8e191dac7110a914bdde1cec888ff9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402334"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

使用之後[_CrtSetReportMode](crtsetreportmode.md)指定 **_CRTDBG_MODE_FILE**，您可以指定要接收的訊息文字的檔案控制代碼。 **_CrtSetReportFile**也會使用[_CrtDbgReport、 _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)指定的文字 （僅限偵錯版本） 的目的地。

## <a name="syntax"></a>語法

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>參數

*reportType*<br/>
報告類型： **_CRT_WARN**， **_CRT_ERROR**，和 **_CRT_ASSERT**。

*reportFile*<br/>
新的報表檔案*reportType*。

## <a name="return-value"></a>傳回值

成功完成， **_CrtSetReportFile**傳回先前的報表檔案中指定的報表類型的定義*reportType*。 如果無效的值傳入*reportType*，此函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式 **_CRTDBG_HFILE_ERROR**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_CrtSetReportFile**搭配[_CrtSetReportMode](crtsetreportmode.md)函式定義的目的地或針對特定報表類型所產生的目的地 **_CrtDbgReport**。 當 **_CrtSetReportMode**呼叫指派 **_CRTDBG_MODE_FILE** reporting 模式的特定報表類型， **_CrtSetReportFile**然後呼叫以定義特定檔案或使用做為目的地的資料流。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，呼叫 **_CrtSetReportFile**會在前置處理期間移除。

下列清單顯示可用的選項，如*reportFile*和所產生的行為的 **_CrtDbgReport**。 這些選項在 Crtdbg.h 中定義為位元旗標。

- **檔案控制代碼**

   將作為訊息目的地的檔案控制代碼。 不會嘗試驗證此控制代碼的有效性。 您必須開啟和關閉檔案控制代碼。 例如: 

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   將訊息寫入至**stderr**，其可重新導向，如下所示：

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   將訊息寫入至**stdout**，其中您可以重新導向。

- **_CRTDBG_REPORT_FILE**

   傳回目前的報表模式。

可個別控制每個報表類型所使用的報表檔案。 例如，便可指定*reportType*的 **_CRT_ERROR**回報給**stderr**，雖然*reportType* 的 **_CRT_ASSERT**回報到使用者定義的檔案控制代碼或資料流。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 在主控台中，與相關聯的標準資料流控制代碼**stdin**， **stdout**，和**stderr**，必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們,. 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**程式庫：** 僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
