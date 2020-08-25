---
title: _spawnvp、_wspawnvp
ms.date: 4/2/2020
api_name:
- _wspawnvp
- _spawnvp
- _o__spawnvp
- _o__wspawnvp
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wspawnvp
- _spawnvp
- wspawnvp
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
ms.openlocfilehash: 2cd1c0e464fe7efb1cce5ba969b34d040b099efa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831329"
---
# <a name="_spawnvp-_wspawnvp"></a>_spawnvp、_wspawnvp

建立處理序並加以執行。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _spawnvp(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnvp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>參數

*mode*<br/>
呼叫此處理序的執行模式。

*cmdname*<br/>
待執行檔案的路徑。

*argv*<br/>
引數指標的陣列。 引數 *argv*[0] 通常是實際模式中的路徑或受保護模式中程式名稱的指標，而 *argv*[1] 透過 *argv*[**n**] 是形成新引數清單之字元字串的指標。 引數 *argv*[**n** + 1] 必須是 **Null** 指標，才能標記引數清單的結尾。

## <a name="return-value"></a>傳回值

從同步 **_spawnvp** 或 **_wspawnvp** (**_P_WAIT** 為 *模式*) 指定的傳回值是新進程的結束狀態。 非同步 **_spawnvp** 或 **_wspawnvp** (**_P_NOWAIT** 或 **_P_NOWAITO** 為 *模式*) 指定的傳回值是進程控制碼。 如果處理序正常終止，結束狀態為 0。 如果產生的進程明確使用非零的引數來呼叫 **結束常式，** 您可以將結束狀態設為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 傳回值-1 表示) 不啟動新進程 (錯誤。 在此情況下， **errno** 會設定為下列其中一個值：

| 值 | 描述 |
|-|-|
| **E2BIG** | 引數清單超過 1024 個位元組。 |
| **EINVAL** | *模式* 引數無效。 |
| **ENOENT** | 找不到檔案或路徑。 |
| **ENOEXEC** | 指定的檔案無法執行或可執行檔格式無效。 |
| **ENOMEM** | 可用記憶體不足，無法執行新處理序。 |

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

這些函式中的每一個都會建立新的處理常式並加以執行，並將指標陣列傳遞至命令列引數，並使用 **PATH** 環境變數尋找要執行的檔案。

這些函式會驗證它們的參數。 如果 *cmdname* 或 *argv* 是 null 指標，或如果 *argv* 指向 null 指標，或 *argv*[0] 是空字串，則會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 **errno** 設定為 **EINVAL**，並傳回-1。 未繁衍任何新處理序。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_spawnvp**|\<stdio.h> 或 \<process.h>|
|**_wspawnvp**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
