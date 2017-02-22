---
title: "_onexit，_onexit_m | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_onexit"
  - "_onexit_m"
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
  - "_onexit"
  - "onexit_m"
  - "onexit"
  - "_onexit_m"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "onexit 函式"
  - "登錄，註冊結束常式"
  - "_onexit_m 函式"
  - "onexit_m 函式"
  - "_onexit 函式"
  - "註冊結束常式"
  - "註冊以便在結束時呼叫"
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _onexit，_onexit_m
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

註冊要呼叫的常式結束時間。  
  
## 語法  
  
```  
_onexit_t _onexit(  
   _onexit_t function  
);  
_onexit_t_m _onexit_m(  
   _onexit_t_m function  
);  
```  
  
#### 參數  
 `function`  
 指向函式的指標在結束被呼叫。  
  
## 傳回值  
 `_onexit` 傳回函式指標，如果成功則傳回 `NULL` ，如果沒有，則儲存函式指標的空間。  
  
## 備註  
 `_onexit` 函式會傳遞 \(`function`\) 所呼叫的函式位址，當程式通常時結束。  成功呼叫`_onexit`會以LIFO\(後進先出\)順序產生執行目前函式的暫存器。  函式會傳遞至 `_onexit` 不能接受參數。  
  
 在這種情況下，當`_onexit`被DLL呼叫時，`_onexit`註冊的常式會在DLL\_PROCESS\_DETACH呼叫`DllMain`後在DLL卸載上執行。  
  
 `_onexit` 是一種Microsoft延伸。  若為 ANSI 可攜性，請使用 [atexit](../../c-runtime-library/reference/atexit.md)。  函式的 `_onexit_m` 版本是使用混合模式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_onexit`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_onexit.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
/* Prototypes */  
int fn1(void), fn2(void), fn3(void), fn4 (void);  
  
int main( void )  
{  
   _onexit( fn1 );  
   _onexit( fn2 );  
   _onexit( fn3 );  
   _onexit( fn4 );  
   printf( "This is executed first.\n" );  
}  
  
int fn1()  
{  
   printf( "next.\n" );  
   return 0;  
}  
  
int fn2()  
{  
   printf( "executed " );  
   return 0;  
}  
  
int fn3()  
{  
   printf( "is " );  
   return 0;  
}  
  
int fn4()  
{  
   printf( "This " );  
   return 0;  
}  
```  
  
## Output  
  
```  
This is executed first.  
This is executed next.  
```  
  
## .NET Framework 對等用法  
 [System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_\_dllonexit](../../c-runtime-library/dllonexit.md)