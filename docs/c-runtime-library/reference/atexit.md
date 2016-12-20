---
title: "atexit | Microsoft Docs"
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
  - "atexit"
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
apitype: "DLLExport"
f1_keywords: 
  - "atexit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "atexit 函式"
  - "處理, 在結束時"
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atexit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理指定的函式在匯出。  
  
## 語法  
  
```  
int atexit(  
   void (__cdecl *func )( void )  
);  
```  
  
#### 參數  
 `func`  
 要呼叫的函式。  
  
## 傳回值  
 `atexit` 會傳回 0，如果成功則為非零值，則會發生錯誤。  
  
## 備註  
 `atexit` 函式會傳遞 \(`func`\) 所呼叫的函式位址，當程式通常時結束。  對 `atexit` 的後續呼叫會執行目前函式的暫存器，初始 \(LIFO\) 命令。  函式會傳遞至 `atexit` 不能接受參數。  `atexit` 和 `_onexit` 使用堆積保留函式暫存器。  因此，可以註冊函式數目由堆積記憶體的限制。  
  
 在 `atexit` 函式中的程式碼不應該包含在可能已經卸載的任何 DLL 的任何相依性，在呼叫 `atexit` 函式時。  
  
 若要產生 ANSI 相容的應用程式，請使用 ANSI 標準 `atexit` 函式 \(而不是相同的 `_onexit` 函式\)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`atexit`|\<stdlib.h\>|  
  
## 範例  
 在呼叫 `atexit` 時，這個程式推入執行的堆疊的四個函式上。  當程式結束，這些程式會在為時執行，第一個基礎。  
  
```  
// crt_atexit.c  
#include <stdlib.h>  
#include <stdio.h>  
  
void fn1( void ), fn2( void ), fn3( void ), fn4( void );  
  
int main( void )  
{  
   atexit( fn1 );  
   atexit( fn2 );  
   atexit( fn3 );  
   atexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
void fn1()  
{  
   printf( "next.\n" );  
}  
  
void fn2()  
{  
   printf( "executed " );  
}  
  
void fn3()  
{  
   printf( "is " );  
}  
  
void fn4()  
{  
   printf( "This " );  
}  
```  
  
  **這會先執行。**  
**這是執行的下一個。**   
## .NET Framework 對等用法  
 [System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)