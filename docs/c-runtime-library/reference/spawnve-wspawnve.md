---
title: _spawnve、_wspawnve
ms.date: 11/04/2016
api_name:
- _spawnve
- _wspawnve
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
- wspawnve
- _spawnve
- _wspawnve
helpviewer_keywords:
- _spawnve function
- spawnve function
- wspawnve function
- processes, creating
- _wspawnve function
- processes, executing new
- process creation
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
ms.openlocfilehash: 37f8b6737fbd2b36c1482790a34dc386936b704b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442709"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve、_wspawnve

建立和執行新處理序。

> [!IMPORTANT]
> 這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _spawnve(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnve(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>參數

*mode*<br/>
呼叫處理序的執行模式。

*cmdname*<br/>
待執行檔案的路徑。

*argv*<br/>
引數指標的陣列。 引數*argv*[0] 通常是真實模式中的路徑或受保護模式中程式名稱的指標，而*argv*[1] 透過*argv*[**n**] 則是形成新引數清單之字元字串的指標。 引數*argv*[**n** + 1] 必須是**Null**指標，以標記引數清單的結尾。

*envp*<br/>
環境設定的指標陣列。

## <a name="return-value"></a>傳回值

同步 **_spawnve**或 **_wspawnve** （ **_P_WAIT**為*模式*指定）的傳回值是新進程的結束狀態。 非同步 **_spawnve**或 **_wspawnve** （為*模式*指定的 **_P_NOWAIT**或 **_P_NOWAITO** ）的傳回值是進程控制碼。 如果處理序正常終止，結束狀態為 0。 如果產生的進程特別呼叫具有非零引數的**exit**常式，您可以將結束狀態設定為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 傳回值-1 表示發生錯誤（新的進程未啟動）。 在此情況下， **errno**會設定為下列其中一個值。

|||
|-|-|
| **E2BIG** | 引數清單超過 1024 個位元組。 |
| **EINVAL** | *模式*引數無效。 |
| **ENOENT** | 找不到檔案或路徑。 |
| **ENOEXEC** | 指定的檔案無法執行或可執行檔格式無效。 |
| **ENOMEM** | 可用記憶體不足，無法執行新處理序。 |

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會建立並執行新處理序，並將指標陣列傳遞至命令列引數，將指標陣列傳處至環境設定。

這些函式會驗證它們的參數。 如果*cmdname*或*argv*是 null 指標，或是*argv*指向 null 指標，或*argv*[0] 是空字串，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL**，並傳回-1。 未繁衍任何新處理序。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> 或 \<process.h>|
|**_wspawnve**|\<stdio.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
