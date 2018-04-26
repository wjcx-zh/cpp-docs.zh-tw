---
title: _execlp、_wexeclp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wexeclp
- _execlp
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wexeclp
- wexeclp
- _execlp
dev_langs:
- C++
helpviewer_keywords:
- execlp function
- _execlp function
- _wexeclp function
- wexeclp function
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 460b37a2c9e14536efa56e6a4d27c74efee7799a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="execlp-wexeclp"></a>_execlp、_wexeclp

載入並執行新的子處理序。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _execlp(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexeclp(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>參數

*cmdname*<br/>
待執行檔案的路徑。

*arg0*，...*argn*<br/>
參數指標的清單。

## <a name="return-value"></a>傳回值

如果成功的話，這些函式不會傳回呼叫處理序。 傳回值-1 表示錯誤，在此情況下**errno**設定全域變數。

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

所有這些函式載入並執行新處理序，每個命令列引數作為個別參數傳遞，並使用**路徑**環境變數尋找要執行的檔案。

**_Execlp**函式會驗證它們的參數。 如果*cmdname*或*arg0*是 null 指標或空字串，這些函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回-1。 未啟動任何新的處理序。

## <a name="requirements"></a>需求

|功能|必要的標頭|選擇性標頭|
|--------------|---------------------|---------------------|
|**_execlp**|\<process.h>|\<errno.h>|
|**_wexeclp**|\<process.h> 或 \<wchar.h>|\<errno.h>|

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
