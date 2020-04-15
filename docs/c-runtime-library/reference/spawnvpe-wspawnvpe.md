---
title: _spawnvpe、_wspawnvpe
ms.date: 4/2/2020
api_name:
- _spawnvpe
- _wspawnvpe
- _o__spawnvpe
- _o__wspawnvpe
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
- _spawnvpe
- wspawnvpe
- _wspawnvpe
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
ms.openlocfilehash: c8a97e99711a2053a26ae850c09c82a4342cda3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355718"
---
# <a name="_spawnvpe-_wspawnvpe"></a>_spawnvpe、_wspawnvpe

建立和執行新處理序。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _spawnvpe(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnvpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>參數

*模式*<br/>
呼叫處理序的執行模式

*cmdname*<br/>
要執行之檔案的路徑

*argv*<br/>
引數指標的陣列。 參數*argv*{0} 通常是指向實際模式下的路徑或受保護模式下的程式名稱的指標 *,argv*[1] 到*argv*=**n**= 是指向構成新參數清單的字串的指標。 參數*argv*=**n** [1] 必須是**NULL**指標,以標記參數清單的末尾。

*envp*<br/>
環境設定的指標陣列

## <a name="return-value"></a>傳回值

來自同步 **_spawnvpe**或 **_wspawnvpe(_P_WAIT**為*模式*指定的 **)** 的返回值是新進程的退出狀態。 來自非同步 **_spawnvpe**或 **_wspawnvpe(_P_NOWAIT**或 **_wspawnvpe**為*模式*指定的 **_P_NOWAITO)** 的傳回值是進程句柄。 如果處理序正常終止，結束狀態為 0。 如果生成的進程專門使用非零參數調用**退出**例程,則可以將退出狀態設置為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 返回值 -1 表示錯誤(未啟動新進程)。 在這種情況下 **,errno**設定為以下值之一:

|||
|-|-|
| **E2BIG** | 引數清單超過 1024 個位元組。 |
| **埃因瓦爾** | *模式*參數無效。 |
| **埃諾恩特** | 找不到檔案或路徑。 |
| **ENOEXEC** | 指定的檔案無法執行或可執行檔格式無效。 |
| **ENOMEM** | 可用記憶體不足，無法執行新處理序。 |

有關這些代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

所有這些函式都會建立並執行新處理序，並將指標陣列傳遞至命令列引數，將指標陣列傳處至環境設定。 這些函數使用**PATH**環境變數來查找要執行的檔。

這些函式會驗證它們的參數。 如果*cmdname*或*argv*是空指標,或者如果*argv*指向空指標,或者*argv*[0] 是空字串,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**errno**設置為**EINVAL**,並返回 -1。 未繁衍任何新處理序。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h> 或 \<process.h>|
|**_wspawnvpe**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。

## <a name="see-also"></a>另請參閱

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
