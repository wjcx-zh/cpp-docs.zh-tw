---
title: system、_wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 15e4637d709fdf4600ecb4c66c7d4a75c4fa07eb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844973"
---
# <a name="system-_wsystem"></a>system、_wsystem

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

如果 *命令* 為 **Null** ，且找到命令直譯器，則會傳回非零值。 如果找不到命令直譯器，則會傳回0，並將 **errno** 設定為 **ENOENT**。 如果 *命令* 不是 **Null**， **系統** 會傳回命令直譯器所傳回的值。 只有當命令解譯器傳回為 0 的值，它才會傳回為 0 的值。 傳回值-1 表示錯誤，且 **errno** 設定為下列其中一個值：

| 值 | 描述 |
|-|-|
| **E2BIG** | 引數清單 (依系統而定) 太大。 |
| **ENOENT** | 找不到命令解譯器。 |
| **ENOEXEC** | 無法執行命令解譯器檔案，因為此格式無效。 |
| **ENOMEM** | 沒有足夠的記憶體可用來執行命令；可用的記憶體已損毀；或存在非無效的區塊，表示未正確配置執行此呼叫的處理序。 |

如需這些傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**系統**函式會將*命令*傳遞至命令直譯器，它會以作業系統命令的形式執行字串。 **系統** 會使用 **COMSPEC** 和 **PATH** 環境變數來找出 CMD.exe 的命令直譯器檔案。 如果 *命令* 為 **Null**，則函式只會檢查命令直譯器是否存在。

您必須明確地排清、使用 [>fflush](fflush.md) 或 [_flushall](flushall.md)，或在呼叫 **系統**之前關閉任何資料流程。

**_wsystem**是**系統**的寬字元版本;**_wsystem**的*命令*引數是寬字元字串。 除此之外，這些函式的行為相同。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**系統**|**系統**|**_wsystem**|

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**系統**|\<process.h> 或 \<stdlib.h>|
|**_wsystem**|\<process.h>、\<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

這個範例會使用 **系統** 來輸入文字檔。

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>輸入：crt_system.txt

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

[流程式控制制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec，_wexec 函數](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn，_wspawn 函數](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
