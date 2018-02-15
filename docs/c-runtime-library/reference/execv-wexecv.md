---
title: "_execv、_wexecv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wexecv
- _execv
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
- _execv
- _wexecv
- wexecv
dev_langs:
- C++
helpviewer_keywords:
- _wexecv function
- _execv function
- wexecv function
- execv function
ms.assetid: 8dbaf7bc-9040-4316-a0c1-db7e866b52af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9520c8975d342b423bf61a1f5973a4bdabfcc37
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="execv-wexecv"></a>_execv、_wexecv
載入並執行新的子處理序。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱[通用 Windows 平台應用程式不支援 CRT 函式](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>語法  
  
```  
intptr_t _execv(   
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wexecv(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### <a name="parameters"></a>參數  
 `cmdname`  
 待執行檔案的路徑。  
  
 `argv`  
 參數指標的陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，這些函式不會傳回呼叫處理序。 傳回值-1 表示錯誤，在此情況下`errno`設定全域變數。  
  
|`errno` 值|描述|  
|-------------------|-----------------|  
|`E2BIG`|引數和環境設定所需的空間超過 32 KB。|  
|`EACCES`|指定的檔案具有鎖定或共用違規。|  
|`EINVAL`|無效的參數。|  
|`EMFILE`|開啟太多檔案 (必須開啟指定的檔案，藉此判斷是否為可執行檔)。|  
|`ENOENT`|找不到檔案或路徑。|  
|`ENOEXEC`|指定的檔案無法執行或可執行檔格式無效。|  
|`ENOMEM`|沒有足夠的記憶體可用來執行新處理序；可用的記憶體已損毀；或存在無效的區塊，表示未正確配置呼叫的處理序。|  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 所有這些函式都會載入並執行新的處理序，並將指標陣列傳遞至命令列引數。  
  
 `_execv` 函式會驗證它們的參數。 如果 `cmdname` 為 Null 指標，或如果 `argv` 為 Null 指標 (空陣列的指標)，或如果陣列包含作為第一個引數的空字串，則 `_execv` 函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` ，並傳回 -1。 未啟動任何處理序。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------------|---------------------|---------------------|  
|`_execv`|\<process.h>|\<errno.h>|  
|`_wexecv`|\<process.h> 或 \<wchar.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)中的範例。  
  
## <a name="see-also"></a>請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)