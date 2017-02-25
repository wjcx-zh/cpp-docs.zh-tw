---
title: "時鐘 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "clock"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "clock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "計算已使用的處理器時間"
  - "clock 函式"
  - "已使用的處理器時間"
  - "已使用的處理器時間, 計算"
  - "時間, 計算處理器"
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# 時鐘
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

計算所呼叫的處理序使用的時鐘時間。  
  
## 語法  
  
```  
clock_t clock( void );  
```  
  
## 傳回值  
 自此處理序開始後耗用的時鐘時間 \(以秒為單位的時間的耗用時間 `CLOCKS_PER_SEC`\)。  如果耗用時間量無法使用，則此函式會傳回 – 1，轉換為 `clock_t`。  
  
## 備註  
 `clock` 函式會告知呼叫處理序已使用多少時鐘時間。  請注意這並未完全符合 ISO C99 \(ISO C99 指定淨 CPU 時間為傳回值\)。  若要取得 CPU 時間，請使用 Win32 [GetProcessTimes](http://msdn.microsoft.com/library/windows/desktop/ms683223) 函式。  
  
 計時器刻度大約等於 1\/`CLOCKS_PER_SEC` 秒。  只要有足夠的時間，`clock` 所傳回的值可超過 `clock_t` 的最大正值，因此變成負數，或超過最大絕對值因而換用。  在處理序中，請勿依賴執行多於 214,748 秒 \(或大約 59 小時\) 的總耗用時間值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`clock`|\<time.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_clock.c  
// This example prompts for how long  
// the program is to run and then continuously  
// displays the elapsed time for that period.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
void sleep( clock_t wait );  
  
int main( void )  
{  
   long    i = 6000000L;  
   clock_t start, finish;  
   double  duration;  
  
   // Delay for a specified time.  
   printf( "Delay for three seconds\n" );  
   sleep( (clock_t)3 * CLOCKS_PER_SEC );  
   printf( "Done!\n" );  
  
   // Measure the duration of an event.  
   printf( "Time to do %ld empty loops is ", i );  
   start = clock();  
   while( i-- )   
      ;  
   finish = clock();  
   duration = (double)(finish - start) / CLOCKS_PER_SEC;  
   printf( "%2.1f seconds\n", duration );  
}  
  
// Pauses for a specified number of milliseconds.  
void sleep( clock_t wait )  
{  
   clock_t goal;  
   goal = wait + clock();  
   while( goal > clock() )  
      ;  
}  
```  
  
  **延遲三秒鐘**  
**完成！  執行 6000000 空的迴圈所需時間為 0.1 秒**    
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [difftime、\_difftime32、\_difftime64](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)