---
title: "_ftime_s、_ftime32_s、_ftime64_s | Microsoft Docs"
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
  - "_ftime_s"
  - "_ftime64_s"
  - "_ftime32_s"
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
  - "_ftime_s"
  - "_ftime64_s"
  - "ftime_s"
  - "_ftime32_s"
  - "ftime32_s"
  - "ftime64_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ftime32_s 函式"
  - "ftime_s 函式"
  - "_ftime64_s 函式"
  - "目前時間"
  - "ftime64_s 函式"
  - "時間，取得目前的"
  - "_ftime_s 函式"
  - "_ftime32_s 函式"
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ftime_s、_ftime32_s、_ftime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得目前的時間。 這些是舊版 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### 參數  
 `timeptr`  
 指標 `_timeb,``__timeb32`, ，或 `__timeb64` 結構。  
  
## 傳回值  
 如果成功，失敗的錯誤代碼。 如果 `timeptr` 為 `NULL`，則傳回值是 `EINVAL`。  
  
## 備註  
 `_ftime_s` 函式取得目前的當地時間，並將它儲存在結構中所指 `timeptr`*。*`_timeb,``__timeb32`,，和`__timeb64` SYS\\Timeb.h 中所定義的結構。 它們包含下表中所列出的四個欄位。  
  
 `dstflag`  
 若日光節約時間已目前生效的當地時區為非零。 \(請參閱 [\_tzset](../../c-runtime-library/reference/tzset.md) 如需說明如何判斷日光節約時間。\)  
  
 `millitm`  
 為以毫秒為單位的秒數部分。  
  
 `time`  
 時間 （秒） 午夜 \(00: 00:00\)、 1970 年 1 月 1 日國際標準時間 \(UTC\)。  
  
 `timezone`  
 以分鐘為單位的差異進時，切換 UTC 與本地時間。 值 `timezone` 設定全域變數的值從 `_timezone` \(請參閱 `_tzset`\)。  
  
 `_ftime64_s`, 它會使用 `__timeb64` 結構，可讓檔案建立日期來表示總 23:59:59，3000 年 12 月 31 日 UTC; 而 `_ftime32_s` 只代表 23:59:59 2038 年 1 月 18 日 UTC 日期。 午夜過後，1970 年 1 月 1 日是所有這些函式的日期範圍的下限。  
  
 `_ftime_s` 相當於 `_ftime64_s` 和 `_timeb` 包含 64 位元時間。 也是如此除非 \_`USE_32BIT_TIME_T` 定義，在此情況下舊的行為是作用中; \_`ftime_s` 會使用 32 位元時間和 `_timeb` 包含 32 位元時間。  
  
 `_ftime_s` 會驗證其參數。 如果傳遞 null 做為指標 `timeptr`, ，函式叫用無效參數處理常式中所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會將 `errno` 到 `EINVAL`。  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`_ftime_s`|\< s \> 和 \< sys\/timeb.h \>|  
|`_ftime32_s`|\< s \> 和 \< sys\/timeb.h \>|  
|`_ftime64_s`|\< s \> 和 \< sys\/timeb.h \>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## 範例  
  
```  
// crt_ftime64_s.c  
// This program uses _ftime64_s to obtain the current  
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
  
   _ftime64_s( &timebuffer );  
  
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
  
```Output  
自 1970 年 1 月 1 日 (UTC) 的秒數︰ 1051553334 毫秒︰ 230 UTC 與本地時間之間的分鐘︰ 480 日光節約時間的旗標 （1 代表日光節約時間已生效）︰ 1 的時間是星期一 4 月 28 日 11:08:54.230 2003年  
```  
  
## .NET Framework 對等用法  
 [System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)