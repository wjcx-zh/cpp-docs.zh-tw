---
title: system、_wsystem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- system
- _wsystem
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tsystem
- _wsystem
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca44648ed378d4484b8e4c32a38a6780b3eddd53
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="system-wsystem"></a>system、_wsystem

執行命令。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>參數

*command*<br/>
要執行的命令。

## <a name="return-value"></a>傳回值

如果*命令*是**NULL**並找到命令解譯器，傳回非零值。 如果找不到命令解譯器，會傳回 0，並設定**errno**至**ENOENT**。 如果*命令*不**NULL**，**系統**傳回命令解譯器所傳回的值。 只有當命令解譯器傳回為 0 的值，它才會傳回為 0 的值。 傳回值為-1 表示錯誤，和**errno**設為下列值之一：

|||
|-|-|
**E2BIG**|引數清單 (依系統而定) 太大。
**ENOENT**|找不到命令解譯器。
**ENOEXEC**|無法執行命令解譯器檔案，因為此格式無效。
**ENOMEM**|沒有足夠的記憶體可用來執行命令；可用的記憶體已損毀；或存在非無效的區塊，表示未正確配置執行此呼叫的處理序。

如需這些傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**系統**函式傳遞*命令*給命令解譯器，它會執行與作業系統命令的字串。 **系統**使用**COMSPEC**和**路徑**環境變數，以找出命令解譯器檔案 CMD.exe。 如果*命令*是**NULL**，函式只會檢查命令解譯器是否存在。

您必須明確清除，使用[fflush](fflush.md)或[_flushall](flushall.md)，或呼叫之前先關閉所有資料流**系統**。

**_wsystem**是寬字元版本的**系統**;*命令*引數 **_wsystem**是寬字元字串。 除此之外，這些函式的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**system**|\<process.h> 或 \<stdlib.h>|
|**_wsystem**|\<process.h> 或 \<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

這個範例會使用**系統**輸入文字檔案。

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crtsystemtxt"></a>輸入：crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
Line one.
Line two.
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
