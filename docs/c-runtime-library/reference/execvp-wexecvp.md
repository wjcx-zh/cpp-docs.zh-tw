---
title: _execvp、_wexecvp
ms.date: 11/04/2016
api_name:
- _execvp
- _wexecvp
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execvp
- wexecvp
- _wexecvp
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
ms.openlocfilehash: 60de62a61c78152cd4a2d8053da41a37a4091424
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941795"
---
# <a name="_execvp-_wexecvp"></a>_execvp、_wexecvp

載入並執行新的子處理序。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _execvp(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecvp(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>參數

*cmdname*<br/>
待執行檔案的路徑。

*argv*<br/>
參數指標的陣列。

## <a name="return-value"></a>傳回值

如果成功的話，這些函式不會傳回呼叫處理序。 傳回值-1 表示發生錯誤，在此情況下會設定**errno**全域變數。

|**errno**值|描述|
|-------------------|-----------------|
|**E2BIG**|引數和環境設定所需的空間超過 32 KB。|
|**EACCES**|指定的檔案具有鎖定或共用違規。|
|**EINVAL**|無效的參數。|
|**EMFILE**|開啟太多檔案 (必須開啟指定的檔案，藉此判斷是否為可執行檔)。|
|**ENOENT**|找不到檔案或路徑。|
|**ENOEXEC**|指定的檔案無法執行或可執行檔格式無效。|
|**ENOMEM**|沒有足夠的記憶體可用來執行新處理序；可用的記憶體已損毀；或存在無效的區塊，表示未正確配置呼叫的處理序。|

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會載入並執行新的進程，將指標陣列傳遞至命令列引數，並使用**PATH**環境變數尋找要執行的檔案。

**_Execvp**函數會驗證它們的參數。 如果*cmdname*為 null 指標，或*argv*為 null 指標、指向空陣列的指標，或如果陣列包含空字串做為第一個引數，則這些函式會叫用不正確參數處理常式，如[參數驗證中所述](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行, 這些函式會將**errno**設定為**EINVAL** , 並傳回-1。 未啟動任何處理序。

## <a name="requirements"></a>需求

|函數|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_execvp**|\<process.h>|\<errno.h>|
|**_wexecvp**|\<process.h> 或 \<wchar.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
