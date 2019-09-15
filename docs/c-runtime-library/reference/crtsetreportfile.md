---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942285"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

使用[_CrtSetReportMode](crtsetreportmode.md)指定 **_CRTDBG_MODE_FILE**之後，您可以指定要接收郵件內文的檔案控制代碼。 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)也會使用 **_CrtSetReportFile**來指定文字的目的地（僅限偵錯工具版本）。

## <a name="syntax"></a>語法

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>參數

*reportType*<br/>
報表類型： **_CRT_WARN**、 **_CRT_ERROR**和 **_CRT_ASSERT**。

*reportFile*<br/>
*ReportType*的新報告檔。

## <a name="return-value"></a>傳回值

成功完成時， **_CrtSetReportFile**會傳回先前針對*reportType*中指定之報表類型所定義的報表檔案。 如果針對*reportType*傳入了不正確值，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回 **_CRTDBG_HFILE_ERROR**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_CrtSetReportFile**會與[_CrtSetReportMode](crtsetreportmode.md)函數搭配使用，以定義 **_CrtDbgReport**所產生之特定報表類型的目的地或目的地。 呼叫 **_CrtSetReportMode**來指派特定報表類型的 **_CRTDBG_MODE_FILE**報告模式時，應該會呼叫 **_CrtSetReportFile**來定義要當做目的地使用的特定檔案或資料流程。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtSetReportFile**的呼叫。

下列清單顯示*reportFile*的可用選項，以及 **_CrtDbgReport**的結果行為。 這些選項在 Crtdbg.h 中定義為位元旗標。

- **檔案控制代碼**

   將作為訊息目的地的檔案控制代碼。 不會嘗試驗證此控制代碼的有效性。 您必須開啟和關閉檔案控制代碼。 例如：

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

   將訊息寫入**stderr**，其可重新導向如下：

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   將訊息寫入至**stdout**，您可以將它重新導向。

- **_CRTDBG_REPORT_FILE**

   傳回目前的報表模式。

可個別控制每個報表類型所使用的報表檔案。 例如，您可以指定將 **_CRT_ERROR**的*reportType*回報給**Stderr**，而 **_CRT_ASSERT**的*reportType*會回報給使用者定義的檔案控制代碼或資料流程。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

通用 Windows 平臺 (UWP) 應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向, C 執行時間函式才能在 UWP 應用程式中使用它們。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

**磁帶**僅限[CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的 Debug 版本。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
