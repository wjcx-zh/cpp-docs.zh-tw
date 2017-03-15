---
title: clock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- clock
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clock
dev_langs:
- C++
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3a226377499df1747a022325b762b3cdfdd35ea6
ms.lasthandoff: 02/24/2017

---
# <a name="clock"></a>時鐘
計算所呼叫的處理序使用的時鐘時間。  
  
## <a name="syntax"></a>語法  
  
```  
clock_t clock( void );  
```  
  
## <a name="return-value"></a>傳回值  
啟動處理序時自 CRT 初始化以來已耗用的時間 (測量單位：每秒 `CLOCKS_PER_SEC` 單位數)。 如果已耗用時間無法使用，或已超過可記錄為 `clock_t` 類型的最大正時間，則此函式會傳回值 `(clock_t)(-1)`。   
  
## <a name="remarks"></a>備註  
`clock` 函式會告知在處理序啟動期間自 CRT 初始化之後已使用多少時鐘時間。 請注意，此函式未完全符合將淨 CPU 時間指定為傳回值的 ISO C。 若要取得 CPU 時間，請使用 Win32 [GetProcessTimes](https://msdn.microsoft.com/library/windows/desktop/ms683223) 函式。 若要判定已耗用時間 (秒)，請將 `clock` 函式所傳回的值除以巨集 `CLOCKS_PER_SEC`。  
  
只要有足夠的時間，`clock` 所傳回的值可能會超過 `clock_t` 的最大正值。 處理序執行時間較久時，`clock` 所傳回的值一律為 ISO C99 標準 (7.23.2.1) 和 ISO C11 標準 (7.27.2.1) 所指定的 `(clock_t)(-1)`。 Microsoft 會將 `clock_t` 實作為 `long` (帶正負號的 32 位元整數)，而且 `CLOCKS_PER_SEC` 巨集定義為 1000。 這提供最大 `clock` 函式傳回值 2147483.647 秒，或大約 24.8 天。 請不要依賴執行時間超過此時間量之處理序中 `clock` 所傳回的值。 您可以使用 64 位元 `time` 函式或 Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) 函式來記錄處理序多年來的已耗用時間。  

## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`clock`|\<time.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_clock.c  
// This sample uses clock() to 'sleep' for three 
// seconds, then determines how long it takes  
// to execute an empty loop 600000000 times.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
// Pauses for a specified number of milliseconds.  
void do_sleep( clock_t wait )  
{  
   clock_t goal;  
   goal = wait + clock();  
   while( goal > clock() )  
      ;  
}  
  
const long num_loops = 600000000L;

int main( void )  
{  
   long    i = num_loops;  
   clock_t start, finish;  
   double  duration;  
  
   // Delay for a specified time.  
   printf( "Delay for three seconds\n" );  
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );  
   printf( "Done!\n" );  
  
   // Measure the duration of an event.  
   start = clock();  
   while( i-- )   
      ;  
   finish = clock();  
   duration = (double)(finish - start) / CLOCKS_PER_SEC;  
   printf( "Time to do %ld empty loops is ", num_loops );  
   printf( "%2.3f seconds\n", duration );  
}  
```  
  
```Output  
Delay for three seconds  
Done!  
Time to do 600000000 empty loops is 1.354 seconds  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [difftime、_difftime32、_difftime64](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)
