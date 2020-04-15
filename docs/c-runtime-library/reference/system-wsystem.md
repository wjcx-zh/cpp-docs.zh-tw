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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 21ce04d30da80a40a1162dce06ff378150008766
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362794"
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

*命令*<br/>
要執行的命令。

## <a name="return-value"></a>傳回值

如果*命令*為**NULL**並且找到命令解釋器,則傳回非零值。 找不到命令的直譯器,傳回 0 並將**errno**設定到**ENOENT**。 如果*命令*不是**NULL,****則系統**傳回命令直譯器傳回的值。 只有當命令解譯器傳回為 0 的值，它才會傳回為 0 的值。 傳回值 - 1 表示錯誤 **,errno**設定為以下值之一:

|||
|-|-|
| **E2BIG** | 引數清單 (依系統而定) 太大。 |
| **埃諾恩特** | 找不到命令解譯器。 |
| **ENOEXEC** | 無法執行命令解譯器檔案，因為此格式無效。 |
| **ENOMEM** | 沒有足夠的記憶體可用來執行命令；可用的記憶體已損毀；或存在非無效的區塊，表示未正確配置執行此呼叫的處理序。 |

如需這些傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**系統**函數將*命令*傳遞給命令解釋器,命令解釋器將字串作為操作系統命令執行。 **系統**使用**COMSPEC**和**PATH**環境變數來定位命令-解譯器檔 CMD.exe。 如果*命令*為**NULL,** 則函數將只檢查命令解釋器是否存在。

您必須使用[fflush](fflush.md)或[_flushall](flushall.md)顯式刷新,或在調用**系統**之前關閉任何流。

**_wsystem**是一個寬字元版本的**系統**;要 **_wsystem***的命令*參數是寬字元字串。 除此之外，這些函式的行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**系統**|**系統**|**_wsystem**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**系統**|\<process.h> 或 \<stdlib.h>|
|**_wsystem**|\<process.h> 或 \<stdlib.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此範例使用**系統**鍵入文字檔。

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

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
