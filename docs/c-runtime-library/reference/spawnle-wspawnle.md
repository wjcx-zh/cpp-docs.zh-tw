---
title: _spawnle、_wspawnle
ms.date: 11/04/2016
api_name:
- _spawnle
- _wspawnle
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
- _spawnle
- wspawnle
- _wspawnle
helpviewer_keywords:
- spawnle function
- processes, creating
- _wspawnle function
- processes, executing new
- process creation
- wspawnle function
- _spawnle function
ms.assetid: 80308892-2815-49b1-8cca-53894c366f5a
ms.openlocfilehash: 5020c18eb675c40a6e30886f40dd4d8688646b9c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845961"
---
# <a name="_spawnle-_wspawnle"></a>_spawnle、_wspawnle

建立和執行新處理序。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _spawnle(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL,
   const char *const *envp
);
intptr_t _wspawnle(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>參數

*mode*<br/>
呼叫處理序的執行模式。

*cmdname*<br/>
待執行檔案的路徑。

*arg0*、 *arg1*、.。。 *argn*<br/>
引數指標的清單。 *Arg0*引數通常是指向*cmdname*的指標。 引數 *arg1* 至 *argn* 是形成新引數清單之字元字串的指標。 在 *argn*之後，必須有 **Null** 指標以標記引數清單的結尾。

*envp*<br/>
環境設定的指標陣列。

## <a name="return-value"></a>傳回值

從同步 **_spawnle** 或 **_wspawnle** (**_P_WAIT** 為 *模式*) 指定的傳回值是新進程的結束狀態。 非同步 **_spawnle** 或 **_wspawnle** (**_P_NOWAIT** 或 **_P_NOWAITO** 為 *模式*) 指定的傳回值是進程控制碼。 如果處理序正常終止，結束狀態為 0。 如果產生的進程特別以非零的引數呼叫 **結束常式，** 您就可以將結束狀態設為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 傳回值-1 表示) 不啟動新進程 (錯誤。 在此情況下， **errno** 會設定為下列其中一個值。

| 值 | 描述 |
|--|--|
| **E2BIG** | 引數清單超過 1024 個位元組。 |
| **EINVAL** | *模式* 引數無效。 |
| **ENOENT** | 找不到檔案或路徑。 |
| **ENOEXEC** | 指定的檔案無法執行或可執行檔格式無效。 |
| **ENOMEM** | 可用記憶體不足，無法執行新處理序。 |

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會建立和執行新處理序，並將每個命令列引數作為個別參數傳遞，也會將指標的陣列傳遞至環境設定。

這些函式會驗證它們的參數。 如果 *cmdname* 或 *arg0* 是空字串或 null 指標，則會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 **errno** 設定為 **EINVAL**，並傳回-1。 未繁衍任何新處理序。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_spawnle**|\<process.h>|
|**_wspawnle**|\<stdio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[流程式控制制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn，_wspawn 函數](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec，_wexec 函數](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit，_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
