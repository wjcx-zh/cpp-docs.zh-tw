---
title: "_spawnl、_wspawnl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wspawnl"
  - "_spawnl"
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
  - "spawnl"
  - "wspawnl"
  - "_wspawnl"
  - "_spawnl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "spawnl 函式"
  - "處理序，建立"
  - "_spawnl 函式"
  - "處理序，執行新的"
  - "_wspawnl 函式"
  - "wspawnl 函式"
  - "處理序建立"
ms.assetid: dd4584c9-7173-4fc5-b93a-6e7d3c2316d7
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _spawnl、_wspawnl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立和執行新處理序。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
intptr_t _spawnl(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wspawnl(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### 參數  
 `mode`  
 呼叫處理序的執行模式。  
  
 `cmdname`  
 待執行檔案的路徑。  
  
 `arg0, arg1, ... argn`  
 引數指標的清單。`arg0` 引數通常是 `cmdname` 的指標。`arg1` 到 `argn` 的引數是形成新引數清單之字元字串的指標。`argn`之後必須有一個 `NULL` 指標，以標記引數清單的結尾。  
  
## 傳回值  
 同步 `_spawnl` 或 `_wspawnl` \(為 `mode` 指定的 `_P_WAIT`\) 的傳回值是新處理序的結束狀態。 非同步 `_spawnl` 或 `_wspawnl` \(為 `mode` 指定的 `_P_NOWAIT` 或 `_P_NOWAITO`\) 的傳回值是處理序控制代碼。 如果處理序正常終止，結束狀態為 0。 如果繁衍的處理序會用非零的引數明確呼叫 `exit` 常式，您就可以將結束狀態設為非零值。 如果新處理序未明確設定確定的結束狀態，所謂確定的結束狀態表示因中止或中斷而異常結束。 傳回值為 –1 表示錯誤 \(新處理序未啟動\)。 在這種情況下，`errno` 會設為下列其中一個值。  
  
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
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 這些函式會驗證它們的參數。 如果 `cmdname` 或 `arg0` 是空字串或 null 指標，則會叫用無效參數處理常式 \(如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述\)。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 \-1。 未繁衍任何新處理序。  
  
## 備註  
 所有這些函式都會建立和執行新的處理序，並將每個命令列引數作為個別參數傳遞。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_spawnl`|\<process.h\>|  
|`_wspawnl`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)中的範例。  
  
## .NET Framework 對等用法  
  
-   [System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
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