---
title: "_execle、_wexecle | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_execle"
  - "_wexecle"
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
  - "wexecle"
  - "_execle"
  - "_wexecle"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_execle 函式"
  - "_wexecle 函式"
  - "execle 函式"
  - "wexecle 函式"
ms.assetid: 75efa9c5-96b7-4e23-acab-06258901f63a
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _execle、_wexecle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

載入並執行新的子處理序。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
intptr_t _execle(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wexecle(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL,  
   const char *const *envp   
);  
```  
  
#### 參數  
 `cmdname`  
 待執行檔案的路徑。  
  
 `arg0`，`...``argn`  
 參數指標的清單。  
  
 `envp`  
 環境設定之指標的陣列。  
  
## 傳回值  
 如果成功的話，這些函式不會傳回呼叫處理序。  傳回值為 –1 表示錯誤，在此情況下會設定 `errno` 全域變數。  
  
|`errno` 值|描述|  
|---------------|--------|  
|`E2BIG`|引數和環境設定所需的空間超過 32 KB。|  
|`EACCES`|指定的檔案具有鎖定或共用違規。|  
|`EINVAL`|無效的參數。|  
|`EMFILE`|已開啟太多檔案。  \(必須開啟指定的檔案，藉此判斷是否為可執行檔。\)|  
|`ENOENT`|找不到該檔案或路徑。|  
|`ENOEXEC`|指定的檔案無法執行或可執行檔格式無效。|  
|`ENOMEM`|沒有足夠的記憶體可用來執行新處理序；可用的記憶體已損毀；或存在無效的區塊，表示未正確配置呼叫的處理序。|  
  
 如需這些傳回碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 這些函式中的每一個都會載入和執行新處理序，並將每個命令列引數做為個別參數傳遞，也會將指標的陣列傳遞至環境設定。  
  
 `_execle` 函式會驗證它們的參數。  如果 `cmdname` 或 `arg0` 為 null 指標或空字串，則這些函式會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。  未啟動任何新的處理序。  
  
## 需求  
  
|函式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_execle`|\<process.h\>|\<errno.h\>|  
|`_wexecle`|\<process.h\> 或 \<wchar.h\>|\<errno.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)中的範例。  
  
## .NET Framework 對等用法  
  
-   [System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)