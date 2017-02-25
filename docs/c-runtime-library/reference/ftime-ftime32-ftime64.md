---
title: "_ftime、_ftime32、_ftime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftime64"
  - "_ftime"
  - "_ftime32"
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
  - "_ftime32"
  - "_ftime"
  - "_ftime64"
  - "ftime64"
  - "ftime"
  - "ftime32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ftime64 函式"
  - "_ftime64 函式"
  - "目前時間"
  - "_ftime 函式"
  - "ftime 函式"
  - "_ftime32 函式"
  - "ftime32 函式"
  - "時間，取得目前的"
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _ftime、_ftime32、_ftime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得目前時間。  這些函式已有更安全的版本可用，請參閱 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)。  
  
## 語法  
  
```  
void _ftime(   
   struct _timeb *timeptr   
);  
void _ftime32(   
   struct __timeb32 *timeptr   
);  
void _ftime64(   
   struct __timeb64 *timeptr   
);  
```  
  
#### 參數  
 `timeptr`  
 `_timeb`、 `__timeb32`或`__timeb64`結構的指標。  
  
## 備註  
 `_ftime` 函式取得目前本地時間，並儲存它所指向的結構 `timeptr`*。*`_timeb` 、`__timeb32` 和`__timeb64`結構在 SYS\\Timeb.h中定義。  它們包含四個欄位，如下表所列。  
  
 `dstflag`  
 非零，如果日光節約時間是實際上目前本地的時區。\(如需說明日光節約時間如何，請參考 [\_tzset](../../c-runtime-library/reference/tzset.md) 所決定\)。  
  
 `millitm`  
 秒數的分數 \(以毫秒為單位\)。  
  
 `time`  
 秒數 \(從 00:00: 00\)， 1970 年 1 月 1 日， Coordinated Universal Time \(UTC\)。  
  
 `timezone`  
 差異的分鐘，移至西， UTC 與本地時間之間。  `timezone` 的值是從這個全域變數設定 `_timezone` 的值 \(請參閱 `_tzset`\)。  
  
 `_ftime64`，使用 `__timeb64` 結構，允許檔案建立日期透過 UTC 3000 年 12 月 31 日 23:59 : 59來表示；而 `_ftime32` 傳遞只代表日期 UTC 2038 年 1 月 19 日 03:14: 07。  1970 年 1 月 1 日的午夜是這些函式的時間日期範圍的下界。  
  
 `_ftime` 與 `_ftime64` 等價， `_timeb` ，包含 64 位元的時間。  除非定義 `_USE_32BIT_TIME_T` ，此時會是舊版的行為， `_ftime` 使用 32 位元的時間，而 `_timeb` 包含 32 位元的時間。  
  
 `_ftime` 會驗證其參數。  如果傳遞一個空指標如 `timeptr`，則函式叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果執行允許繼續，對 `EINVAL`的函式會設定 `errno` 。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_ftime`|\<sys\/types.h\> 和 \<sys\/timeb.h\>|  
|`_ftime32`|\<sys\/types.h\> 和 \<sys\/timeb.h\>|  
|`_ftime64`|\<sys\/types.h\> 和 \<sys\/timeb.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_ftime.c  
// compile with: /W3  
// This program uses _ftime to obtain the current  
// time and then stores this time in timebuffer.  
  
#include <stdio.h>  
#include <sys/timeb.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _timeb timebuffer;  
   char timeline[26];  
   errno_t err;  
   time_t time1;  
   unsigned short millitm1;  
   short timezone1;  
   short dstflag1;  
  
   _ftime( &timebuffer ); // C4996  
   // Note: _ftime is deprecated; consider using _ftime_s instead  
  
   time1 = timebuffer.time;  
   millitm1 = timebuffer.millitm;  
   timezone1 = timebuffer.timezone;  
   dstflag1 = timebuffer.dstflag;  
  
   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",   
   time1);  
   printf( "Milliseconds: %d\n", millitm1);  
   printf( "Minutes between UTC and local time: %d\n", timezone1);  
   printf( "Daylight savings time flag (1 means Daylight time is in "  
           "effect): %d\n", dstflag1);   
  
   err = ctime_s( timeline, 26, & ( timebuffer.time ) );  
   if (err)  
   {  
       printf("Invalid argument to ctime_s. ");  
   }  
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,  
           &timeline[20] );  
}  
```  
  
  **秒數，從 1970 年 1 月 1 日 \(Coordinated Universal Time，UTC\):1051553334**  
**毫秒：230**   
**UTC 與本地時間之間的分鐘:480**  
**日光節約時間旗標 \(1 表示日光節約時間生效\):1**  
**時間是星期一 4 月 28 日 11:08: 54.230 年 2003**   
## .NET Framework 對等用法  
 [System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)