---
title: "difftime、_difftime32、_difftime64 | Microsoft Docs"
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
  - "_difftime32"
  - "difftime"
  - "_difftime64"
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
  - "_difftime64"
  - "difftime"
  - "difftime64"
  - "_difftime32"
  - "difftime32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_difftime32 函式"
  - "difftime 函式"
  - "時間, 尋找差異"
  - "difftime64 函式"
  - "_difftime64 函式"
  - "difftime32 函式"
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# difftime、_difftime32、_difftime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找兩個時間之間的差異。  
  
## 語法  
  
```  
double difftime(   
   time_t timer1,  
   time_t timer0   
);  
double _difftime32(   
   __time32_t timer1,  
   __time32_t timer0   
);  
double _difftime64(   
   __time64_t timer1,  
   __time64_t timer0   
);  
```  
  
#### 參數  
 `timer1`  
 結束時間。  
  
 `timer0`  
 開始時間。  
  
## 傳回值  
 `difftime` 傳回所經過時間 （秒）， `timer0` 到 `timer1`。 傳回的值是雙精度浮點數。 傳回的值可能是 0，指出錯誤。  
  
## 備註  
 `difftime` 函式會計算兩個時間值之間的差異 `timer0` 和 `timer1`。  
  
 所提供的時間值必須符合的範圍內 `time_t`。`time_t` 64 位元值。 因此，範圍的結尾已擴充 23:59:59 從 UTC 2038 年 1 月 18 日 23:59:59，3000 年 12 月 31 日。 較低範圍的 `time_t` 仍然是 1970 年 1 月 1 日的午夜。  
  
 `difftime` 是內嵌函式會評估結果為 `_difftime32` 或 `_difftime64` 取決於是否 `_USE_32BIT_TIME_T` 定義。 \_difftime32 和 \_difftime64 可以用於直接強制使用特定大小的階段型別。  
  
 這些函式會驗證它們的參數。 如果參數是零或負值，無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函數會傳回 0，並設定 `errno` 到 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`difftime`|\<time.h\>|  
|`_difftime32`|\<time.h\>|  
|`_difftime64`|\<time.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```cpp  
// crt_difftime.c  
// This program calculates the amount of time  
// needed to do a floating-point multiply 100 million times.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
#include <float.h>  
  
double RangedRand( float range_min, float range_max)  
{  
   // Generate random numbers in the half-closed interval  
   // [range_min, range_max). In other words,  
   // range_min <= random number < range_max  
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)  
            + range_min);  
}  
  
int main( void )  
{  
   time_t   start, finish;  
   long     loop;  
   double   result, elapsed_time;  
   double   arNums[3];  
  
   // Seed the random-number generator with the current time so that  
   // the numbers will be different every time we run.  
   srand( (unsigned)time( NULL ) );  
  
   arNums[0] = RangedRand(1, FLT_MAX);  
   arNums[1] = RangedRand(1, FLT_MAX);  
   arNums[2] = RangedRand(1, FLT_MAX);  
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );  
  
   printf( "Multiplying 2 numbers 100 million times...\n" );  
  
   time( &start );  
   for( loop = 0; loop < 100000000; loop++ )  
      result = arNums[loop%3] * arNums[(loop+1)%3];   
   time( &finish );  
  
   elapsed_time = difftime( finish, start );  
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );  
}  
  
```  
  
```Output  
使用隨機浮點數字 1.04749e + 038 2.01482e + 038 1.72737e + 038Multiplying 2 浮點數值 100 百萬次...程式會採用 3 秒。浮點數相乘 2 點 500 百萬次的數字...程式需要 5 秒鐘。  
```  
  
## .NET Framework 對等用法  
 [System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [時間管理](../../c-runtime-library/time-management.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)