---
title: "_fpreset | Microsoft Docs"
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
  - "_fpreset"
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
  - "_fpreset"
  - "fpreset"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fpreset 函式"
  - "浮點數, 重設數學套件"
  - "fpreset 函式"
ms.assetid: f31c6a04-b464-4f07-a7c4-42133360e328
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fpreset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重設浮點套件。  
  
## 語法  
  
```  
void _fpreset( void );  
```  
  
## 備註  
 `_fpreset` 函式重新初始化浮點算術套件。  `_fpreset` 通常搭配 `signal`、 `system`、 `_exec` 或 `_spawn` 函式使用。  如果程式以 `signal` 攔截浮點錯誤信號 \(`SIGFPE`\)，它可以叫用 `_fpreset` 並使用 `longjmp` 從浮點錯誤安全地復原。  
  
 這個函式現在已不建議在 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 下編譯時使用，因為 Common Language Runtime 只支援預設浮點精準度。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fpreset`|\<float.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_fpreset.c  
// This program uses signal to set up a  
// routine for handling floating-point errors.  
  
#include <stdio.h>  
#include <signal.h>  
#include <setjmp.h>  
#include <stdlib.h>  
#include <float.h>  
#include <math.h>  
#include <string.h>  
  
jmp_buf mark;              // Address for long jump to jump to  
int     fperr;             // Global error number  
  
void __cdecl fphandler( int sig, int num );   // Prototypes  
void fpcheck( void );  
  
int main( void )  
{  
   double n1 = 5.0;  
   double n2 = 0.0;  
   double r;  
   int jmpret;  
  
   // Unmask all floating-point exceptions.   
    _control87( 0, _MCW_EM );  
   // Set up floating-point error handler. The compiler  
   // will generate a warning because it expects  
   // signal-handling functions to take only one argument.  
   if( signal( SIGFPE, (void (__cdecl *)(int)) fphandler ) == SIG_ERR )  
    {  
       fprintf( stderr, "Couldn't set SIGFPE\n" );  
       abort();  
    }  
  
   // Save stack environment for return in case of error. First   
   // time through, jmpret is 0, so true conditional is executed.   
   // If an error occurs, jmpret will be set to -1 and false   
   // conditional will be executed.  
   jmpret = setjmp( mark );  
   if( jmpret == 0 )  
   {  
      printf( "Dividing %4.3g by %4.3g...\n", n1, n2 );  
      r = n1 / n2;  
      // This won't be reached if error occurs.  
      printf( "\n\n%4.3g / %4.3g = %4.3g\n", n1, n2, r );  
  
      r = n1 * n2;  
      // This won't be reached if error occurs.  
      printf( "\n\n%4.3g * %4.3g = %4.3g\n", n1, n2, r );  
   }  
   else  
      fpcheck();  
}  
// fphandler handles SIGFPE (floating-point error) interrupt. Note  
// that this prototype accepts two arguments and that the   
// prototype for signal in the run-time library expects a signal   
// handler to have only one argument.  
//  
// The second argument in this signal handler allows processing of  
// _FPE_INVALID, _FPE_OVERFLOW, _FPE_UNDERFLOW, and   
// _FPE_ZERODIVIDE, all of which are Microsoft-specific symbols   
// that augment the information provided by SIGFPE. The compiler   
// will generate a warning, which is harmless and expected.  
  
void fphandler( int sig, int num )  
{  
   // Set global for outside check since we don't want  
   // to do I/O in the handler.  
   fperr = num;  
  
   // Initialize floating-point package. */  
   _fpreset();  
  
   // Restore calling environment and jump back to setjmp. Return   
   // -1 so that setjmp will return false for conditional test.  
   longjmp( mark, -1 );  
}  
  
void fpcheck( void )  
{  
   char fpstr[30];  
   switch( fperr )  
   {  
   case _FPE_INVALID:  
       strcpy_s( fpstr, sizeof(fpstr), "Invalid number" );  
       break;  
   case _FPE_OVERFLOW:  
       strcpy_s( fpstr, sizeof(fpstr), "Overflow" );  
  
       break;  
   case _FPE_UNDERFLOW:  
       strcpy_s( fpstr, sizeof(fpstr), "Underflow" );  
       break;  
   case _FPE_ZERODIVIDE:  
       strcpy_s( fpstr, sizeof(fpstr), "Divide by zero" );  
       break;  
   default:  
       strcpy_s( fpstr, sizeof(fpstr), "Other floating point error" );  
       break;  
   }  
   printf( "Error %d: %s\n", fperr, fpstr );  
}  
```  
  
  **Dividing    5 by    0...**  
**Error 131: Divide by zero**   
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)