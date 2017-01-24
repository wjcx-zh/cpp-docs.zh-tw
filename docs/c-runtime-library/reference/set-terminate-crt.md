---
title: "set_terminate (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "set_terminate"
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
  - "set_terminate"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "例外狀況處理, 終止"
  - "set_terminate 函式"
  - "terminate 函式"
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# set_terminate (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

安裝您自己的終止程序以被 `terminate`呼叫。  
  
## 語法  
  
```  
terminate_function set_terminate(  
   terminate_function termFunction  
);  
```  
  
#### 參數  
 `termFunction`  
 您剛撰寫的終止函式的指標。  
  
## 傳回值  
 讓指標回到 `set_terminate` 註冊的前一個函式，讓先前函式可以還原。  如果先前函式未設定，則傳回值可用來還原預設行為;此值可能為 null。  
  
## 備註  
 `set_terminate` 函式安裝 `termFunction` 做為 `terminate`呼叫的函式。  在擲回例外狀況前，`set_terminate`和C\+\+例外狀況一起使用，並且有可能隨時被呼叫。  `terminate` calls `abort` by default.  You can change this default by writing your own termination function and calling `set_terminate` with the name of your function as its argument.  `terminate` calls the last function given as an argument to `set_terminate`.  After performing any desired cleanup tasks, `termFunction` should exit the program.  If it does not exit \(if it returns to its caller\), `abort` is called.  
  
 In a multithreaded environment, terminate functions are maintained separately for each thread.  Each new thread needs to install its own terminate function.  Thus, each thread is in charge of its own termination handling.  
  
 The `terminate_function` type is defined in EH.H as a pointer to a user\-defined termination function, `termFunction` that returns `void`.  Your custom function `termFunction` can take no arguments and should not return to its caller.  If it does, `abort` is called.  An exception may not be thrown from within `termFunction`.  
  
```  
typedef void ( *terminate_function )( );  
```  
  
> [!NOTE]
>  The `set_terminate` function only works outside the debugger.  
  
 There is a single `set_terminate` handler for all dynamically linked DLLs or EXEs; even if you call `set_terminate` your handler may be replaced by another, or you may be replacing a handler set by another DLL or EXE.  
  
 This function is not supported under **\/clr:pure**.  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`set_terminate`|\<eh.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 See the example for [terminate](../../c-runtime-library/reference/terminate-crt.md).  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_get\_terminate](../../c-runtime-library/reference/get-terminate.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)