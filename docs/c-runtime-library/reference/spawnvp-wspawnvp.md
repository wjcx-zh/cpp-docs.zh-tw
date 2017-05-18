---
title: "_spawnvp、_wspawnvp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wspawnvp
- _spawnvp
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
- _wspawnvp
- _spawnvp
- wspawnvp
dev_langs:
- C++
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 7ed2815a03df5a189193d547e20c03103325f6d6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="spawnvp-wspawnvp"></a>_spawnvp、_wspawnvp
建立處理序並加以執行。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `mode`  
 呼叫此處理序的執行模式。  
  
 `cmdname`  
 待執行檔案的路徑。  
  
 `argv`  
 引數指標的陣列。 引數 `argv`[0] 通常是指向真實模式中的路徑或受保護模式中的程序名稱之指標，而 `argv`[1] 至 `argv`[`n`] 是指向形成新引數清單的字元字串之指標。 引數 `argv`[`n` +1] 必須是 `NULL` 指標，以標記引數清單的結尾。  
  
## <a name="return-value"></a>傳回值  
 同步 `_spawnvp` 或 `_wspawnvp` (為 `mode` 指定的 `_P_WAIT`) 的傳回值是新處理序的結束狀態。 非同步 `_spawnvp` 或 `_wspawnvp` (為`_P_NOWAIT` 指定的 `_P_NOWAITO` 或 `mode`) 的傳回值是處理序控制代碼。 如果處理序正常終止，結束狀態為 0。 如果繁衍的處理序明確使用非零引數呼叫 `exit` 常式，您就可以將結束狀態設為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 傳回值-1 表示的錯誤 （新處理序未啟動）。 在這種情況下， `errno` 會設為下列其中一個值：  
  
 `E2BIG`  
 引數清單超過 1024 個位元組。  
  
 `EINVAL`  
 `mode` 引數無效。  
  
 `ENOENT`  
 找不到檔案或路徑。  
  
 `ENOEXEC`  
 指定的檔案無法執行或可執行檔格式無效。  
  
 `ENOMEM`  
 可用記憶體不足，無法執行新處理序。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 這些函式中的每一個都會產生新程序並加以執行，並且將指標的陣列傳遞至命令列引數，以及使用 `PATH` 環境變數尋找要執行的檔案。  
  
 這些函式會驗證它們的參數。 如果 `cmdname` 或 `argv` 其中之一為 null 指標，或是 `argv` 指向 null 指標，或者如果 `argv[0]` 為空字串，則會叫用無效參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中執行的應用程式。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 -1。 未繁衍任何新處理序。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_spawnvp`|\<stdio.h> 或 \<process.h>|  
|`_wspawnvp`|\<stdio.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。  
  
## <a name="see-also"></a>另請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)
