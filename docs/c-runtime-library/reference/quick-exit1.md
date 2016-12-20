---
title: "quick_exit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "quick_exit"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "quick_exit"
  - "process/quick_exit"
  - "stdlib/quick_exit"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "quick_exit 函式"
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# quick_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引發正常的程式終止。  
  
## 語法  
  
```  
__declspec(noreturn) void quick_exit(  
    int status  
);  
```  
  
#### 參數  
 status  
 要回傳給主機環境的狀態碼。  
  
## 傳回值  
 `quick_exit` 函式無法回傳給其呼叫端。  
  
## 備註  
 `quick_exit` 函式會引發正常程式終止。 其不會呼叫任何由 `atexit`、`_onexit` 所註冊的函式，也不會呼叫 `signal` 函式所註冊的訊號處理常式。 若呼叫 `quick_exit` 多次，或也同時呼叫了 `exit` 函式，其行為不確定。  
  
 `quick_exit` 函式會以後進先出 \(LIFO\) 的順序呼叫由 `at_quick_exit` 所註冊的函式，但不包括此函式註冊時就已呼叫的函式。  若在呼叫先前已註冊，會終止函數呼叫的函式時呼叫 [longjmp](../../c-runtime-library/reference/longjmp.md)，其行為不確定。  
  
 在呼叫了已註冊的函式之後，`quick_exit` 會使用 `status` 值叫用 `_Exit`，將控制權交還給主機環境。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`quick_exit`|\<process.h\> 或 \<stdlib.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)