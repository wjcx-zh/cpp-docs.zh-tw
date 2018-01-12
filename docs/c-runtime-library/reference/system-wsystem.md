---
title: "system、_wsystem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c470717d48836fd405e98f5fccca222e87a9c33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="system-wsystem"></a>system、_wsystem
執行命令。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
int system(  
   const char *command   
);  
int _wsystem(  
   const wchar_t *command   
);  
```  
  
#### <a name="parameters"></a>參數  
 `command`  
 要執行的命令。  
  
## <a name="return-value"></a>傳回值  
 如果 `command` 是 `NULL`，且已找到命令解譯器，則傳回非零的值。 如果找不到該命令解譯器，則會傳回 0，並將 `errno` 設定為 `ENOENT`。 如果 `command` 不是 `NULL`，則 `system` 會傳回命令解譯器所傳回的值。 只有當命令解譯器傳回為 0 的值，它才會傳回為 0 的值。 傳回值為-1 表示錯誤，和`errno`設為下列值之一：  
  
 `E2BIG`  
 引數清單 (依系統而定) 太大。  
  
 `ENOENT`  
 找不到命令解譯器。  
  
 `ENOEXEC`  
 無法執行命令解譯器檔案，因為此格式無效。  
  
 `ENOMEM`  
 沒有足夠的記憶體可用來執行命令；可用的記憶體已損毀；或存在非無效的區塊，表示未正確配置執行此呼叫的處理序。  
  
 如需這些傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `system` 函式會將 `command` 傳遞到命令解譯器，該解譯器將此字串做為作業系統命令執行。 `system` 使用 `COMSPEC` 和 `PATH` 環境變數，以找出命令解譯器檔案 CMD.exe。 如果 `command` 是 `NULL`，則此函式只會檢查命令解譯器是否存在。  
  
 您必須先明確清除 (使用 `fflush` 或 `_flushall`) 或關閉所有資料流，再進行 `system` 函式呼叫。  
  
 `_wsystem` 是寬字元版本的 `system`；`command` 的 `_wsystem` 引數是寬字元字串。 除此之外，這些函式的行為相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsystem`|`system`|`system`|`_wsystem`|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`system`|\<process.h> 或 \<stdlib.h>|  
|`_wsystem`|\<process.h> 或 \<stdlib.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 這個範例會使用 `system` 來「輸入」文字檔案。  
  
```  
// crt_system.c  
  
#include <process.h>  
  
int main( void )  
{  
   system( "type crt_system.txt" );  
}  
```  
  
## <a name="input-crtsystemtxt"></a>輸入：crt_system.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>輸出  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)