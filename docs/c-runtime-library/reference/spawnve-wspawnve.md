---
title: "_spawnve、_wspawnve | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_spawnve"
  - "_wspawnve"
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
  - "wspawnve"
  - "_spawnve"
  - "_wspawnve"
  - "spawnve"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_spawnve 函式"
  - "_wspawnve 函式"
  - "處理序建立"
  - "處理序, 建立"
  - "處理序, 執行新的"
  - "spawnve 函式"
  - "wspawnve 函式"
ms.assetid: 26d1713d-b551-4f21-a07b-e9891a2ae6cf
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _spawnve、_wspawnve
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立和執行新處理序。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
intptr_t _spawnve(  
   int mode,  
   const char *cmdname,  
   const char *const *argv,  
   const char *const *envp   
);  
intptr_t _wspawnve(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *const *argv,  
   const wchar_t *const *envp   
);  
```  
  
#### 參數  
 `mode`  
 呼叫處理序的執行模式。  
  
 `cmdname`  
 待執行檔案的路徑。  
  
 `argv`  
 引數指標的陣列。  引數 `argv`\[0\] 通常是指向路由模式中的路徑或受保護模式中的程序名稱之指標，而 `argv`\[1\] 至 `argv`\[`n`\] 是指向形成新的引數清單的字串。  引數 `argv`\[`n` \+1\] 必須是 `NULL` 指標，以標記引數清單的結尾。  
  
 `envp`  
 指向環境設定的指標的陣列。  
  
## 傳回值  
 同步處理 `_spawnve` 或 `_wspawnve` \(若 `mode` 則為 `_P_WAIT`\) 的傳回值是新處理序的結束狀態。  非同步 `_spawnve` 或 `_wspawnve` 的傳回值 \(若 `mode` 則為 `_P_NOWAITO` 或`_P_NOWAIT` \) 為流程控制代碼。  如果處理序正常終止，結束狀態為 0。  如果繁衍的處理序會用非零的引數明確呼叫 `exit` 常式，您就可以將結束狀態設為非零值。  如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而不正常結束。  傳回值為 –1 表示錯誤 \(新處理序未啟動\)。  在這種情況下，`errno` 會設為下列其中一個值。  
  
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
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 這些函式中建立並執行新處理序，透過指標陣列命令列引數和指標陣列環境設定。  
  
 這些函式會驗證它們的參數。  如果 `cmdname` 或 `argv` 其中之一為 null 指標，或者如果 `argv` 指向 null，或者如果 `argv[0]` 為空字串，則會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。  未繁衍任何新處理序。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_spawnve`|\<stdio.h\> 或 \<process.h\>|  
|`_wspawnve`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。  
  
## .NET Framework 對等用法  
  
-   [System::Diagnostics::Process 類別 \(System::Diagnostics::Process Class\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo 類別 \(System::Diagnostics::ProcessStartInfo Class\)](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)