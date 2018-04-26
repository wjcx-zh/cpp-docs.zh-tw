---
title: _spawnvpe、_wspawnvpe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _spawnvpe
- _wspawnvpe
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
- _spawnvpe
- wspawnvpe
- spawnvpe
- _wspawnvpe
dev_langs:
- C++
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b1498b5772386edb986d3bbd87c63b7c856a3c3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe、_wspawnvpe

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

*mode*<br/>
呼叫處理序的執行模式

*cmdname*<br/>
要執行之檔案的路徑

*argv*<br/>
引數指標的陣列。 引數*argv*[0] 通常是路徑是指向真實模式中或程序名稱在受保護模式中，和*argv*[1] 透過*argv*[**n**] 是指向形成新引數清單之字元字串。 引數*argv*[**n** + 1] 必須是**NULL**指標，以標記引數清單的結尾。

*envp*<br/>
環境設定的指標陣列

## <a name="return-value"></a>傳回值

來自同步的傳回值 **_spawnvpe**或 **_wspawnvpe** (**_P_WAIT**指定*模式*) 是新的結束狀態程序。 傳回值的非同步 **_spawnvpe**或 **_wspawnvpe** (**_P_NOWAIT**或 **_P_NOWAITO**指定*模式*) 是處理序控制代碼。 如果處理序正常終止，結束狀態為 0。 您可以將結束狀態為非零值，如果繁衍的處理序明確呼叫**結束**常式則為非零的引數。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 傳回值-1 表示的錯誤 （新處理序未啟動）。 在此情況下， **errno**設為下列值之一：

|||
|-|-|
**E2BIG**|引數清單超過 1024 個位元組。
**EINVAL**|*模式*引數無效。
**ENOENT**|找不到檔案或路徑。
**ENOEXEC**|指定的檔案無法執行或可執行檔格式無效。
**ENOMEM**|可用記憶體不足，無法執行新處理序。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會建立並執行新處理序，並將指標陣列傳遞至命令列引數，將指標陣列傳處至環境設定。 這些函式使用**路徑**環境變數尋找要執行的檔案。

這些函式會驗證它們的參數。 如果有任一個*cmdname*或*argv*為 null 指標，或如果*argv*指向 null 指標，或*argv*[0] 為空字串，不正確參數叫用處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**，並傳回-1。 未繁衍任何新處理序。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h> 或 \<process.h>|
|**_wspawnvpe**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。

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
