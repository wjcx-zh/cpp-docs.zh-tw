---
title: "_execvp、_wexecvp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_execvp"
  - "_wexecvp"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-process-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_execvp"
  - "wexecvp"
  - "_wexecvp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_execvp 函式"
  - "_wexecvp 函式"
  - "execvp 函式"
  - "wexecvp 函式"
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _execvp、_wexecvp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

載入並執行新的子處理程序。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
intptr_t _execvp(   
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wexecvp(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### 參數  
 `cmdname`  
 欲執行的檔案路徑。  
  
 `argv`  
 參數指標的陣列。  
  
## 傳回值  
 如果成功的話，這些函式將不會回傳給呼叫處理程序。  回傳值 \-1 表示發生錯誤，此時 `errno` 將會被設置。  
  
|`errno` 值|描述|  
|---------------|--------|  
|`E2BIG`|參數和環境設定的空間需求超過 32 KB 。|  
|`EACCES`|指定的檔案發生鎖定或分享衝突。|  
|`EINVAL`|無效參數。|  
|`EMFILE`|開啟太多檔案 \(指定的檔案必須開啟以決定是否可執行\) 。|  
|`ENOENT`|找不到檔案或路徑。|  
|`ENOEXEC`|指定的檔案無法執行或可執行檔格式無效。|  
|`ENOMEM`|執行新的處理程序的可用記憶體不足，可用記憶體已毀損，或存在無效區塊，表示呼叫處理程序沒有被適當地配置。|  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 每個函式載入並執行新程序，傳遞陣列指標至命令列引數並使用`PATH`環境變數以找到要執行的檔案。  
  
 `_execvp` 函式會驗證它們的參數。  如果`cmdname` 是null 指標，或者`argv` 是null指標、空白陣列的指標、或是如果陣列包含空字串作為第一個引數，則這些函式會叫用如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述的無效參數處理常式。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 \-1。  未啟動任何處理序。  
  
## 需求  
  
|Function|必要的標頭|選擇性標頭|  
|--------------|-----------|-----------|  
|`_execvp`|\<process.h\>|\<errno.h\>|  
|`_wexecvp`|\<process.h\> 或 \<wchar.h\>|\<errno.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱在 [\_exec 、 \_wexec 函式 \(\_exec, \_wexec Functions\)](../../c-runtime-library/exec-wexec-functions.md) 的範例。  
  
## .NET Framework 對等用法  
  
-   [System::Diagnostics::Process 類別 \(System::Diagnostics::Process Class\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo 類別 \(System::Diagnostics::ProcessStartInfo Class\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)