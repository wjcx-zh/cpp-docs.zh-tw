---
title: _spawnve、_wspawnve
ms.date: 4/2/2020
api_name:
- _spawnve
- _wspawnve
- _o__spawnve
- _o__wspawnve
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0f546185039bb1503af40d5f690fd8d8c172a679
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355864"
---
# <a name="_spawnve-_wspawnve"></a>_spawnve、_wspawnve

建立和執行新處理序。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

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

*模式*<br/>
呼叫處理序的執行模式。

*cmdname*<br/>
待執行檔案的路徑。

*argv*<br/>
引數指標的陣列。 參數*argv*{0} 通常是指向實際模式下的路徑或受保護模式下的程式名稱的指標 *,argv*[1] 到*argv*=**n**= 是指向構成新參數清單的字串的指標。 參數*argv*=**n** [1] 必須是**NULL**指標,以標記參數清單的末尾。

*envp*<br/>
環境設定的指標陣列。

## <a name="return-value"></a>傳回值

來自同步 **_spawnve**或 **_wspawnve(_P_WAIT**為 **_wspawnve***模式*指定的)的返回值是新進程的退出狀態。 來自非同步 **_spawnve**或 **_wspawnve**的傳回值 **(_P_NOWAIT**或為*模式*指定的 **_P_NOWAITO** )是行程句柄。 如果處理序正常終止，結束狀態為 0。 如果生成的進程專門使用非零參數調用**退出**例程,則可以將退出狀態設置為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 返回值 -1 表示錯誤(未啟動新進程)。 在這種情況下 **,errno**設置為以下值之一。

|||
|-|-|
| **E2BIG** | 引數清單超過 1024 個位元組。 |
| **埃因瓦爾** | *模式*參數無效。 |
| **埃諾恩特** | 找不到檔案或路徑。 |
| **ENOEXEC** | 指定的檔案無法執行或可執行檔格式無效。 |
| **ENOMEM** | 可用記憶體不足，無法執行新處理序。 |

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會建立並執行新處理序，並將指標陣列傳遞至命令列引數，將指標陣列傳處至環境設定。

這些函式會驗證它們的參數。 如果*cmdname*或*argv*是空指標,或者如果*argv*指向空指標,或者*argv*[0] 是空字串,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**errno**設置為**EINVAL**,並返回 -1。 未繁衍任何新處理序。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_spawnve**|\<stdio.h> 或 \<process.h>|
|**_wspawnve**|\<stdio.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
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
