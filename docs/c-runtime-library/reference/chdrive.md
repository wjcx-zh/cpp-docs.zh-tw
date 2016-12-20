---
title: "_chdrive | Microsoft Docs"
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
  - "_chdrive"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "chdrive"
  - "_chdrive"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chdrive 函式"
  - "chdrive 函式"
  - "磁碟機, 變更"
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chdrive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變更目前工作的磁碟機。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### 參數  
 `drive`  
 指定目前可用的磁碟機至 1 到 26 的整數 \(1\=A， 2\=B，依此類推\)。  
  
## 傳回值  
 零 \(0\)，如果成功變更了目前可用的磁碟機；否則為 \-1。  
  
## 備註  
 如果 `drive` 不是範圍從 1 到 26，無效的參數處理常式會被叫用如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行， **\_chdrive** 函式會傳為 \-1，`errno`會設為`EACCES`，且 `_doserrno` 會設為 `ERROR_INVALID_DRIVE`。  
  
 **\_chdrive** 函式不是安全執行緒，因為它是取決於本身不是安全執行緒的 **SetCurrentDirectory** 函式。  若要安全地在多執行緒應用程式使用 **\_chdrive**，您必須提供自己的執行緒同步處理。  如需詳細資訊，請移至[MSDN Library](http://go.microsoft.com/fwlink/?LinkID=150542) 然後搜尋 **SetCurrentDirectory**。  
  
 **\_chdrive** 函式只變更目前執行的磁碟機；**\_chdir** 則變更目前的工作目錄。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**\_chdrive**|\<direct.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱[\_getdrive](../../c-runtime-library/reference/getdrive.md)中的範例。  
  
## .NET Framework 對等用法  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)