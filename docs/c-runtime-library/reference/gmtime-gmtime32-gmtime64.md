---
title: "gmtime、_gmtime32、_gmtime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gmtime32"
  - "gmtime"
  - "_gmtime64"
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
  - "gmtime"
  - "_gmtime32"
  - "_gmtime64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_gmtime32 函式"
  - "_gmtime64 函式"
  - "gmtime 函式"
  - "gmtime32 函式"
  - "gmtime64 函式"
  - "時間函式"
  - "時間結構轉換"
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# gmtime、_gmtime32、_gmtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將時間值轉換成結構。 更安全的版本，這些函式可供使用。請參閱 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)。  
  
## 語法  
  
```  
struct tm *gmtime(   
   const time_t *timer   
);  
struct tm *_gmtime32(   
   const __time32_t *timer   
);  
struct tm *_gmtime64(   
   const __time64_t *timer   
);  
```  
  
#### 參數  
 `timer`  
 指標的預存的時間。 時間表示，如從午夜以來經過的秒 \(00: 00:00\)、 1970 年 1 月 1 日國際標準時間 \(UTC\)。  
  
## 傳回值  
 型別的結構的指標 [tm](../../c-runtime-library/standard-types.md)。 傳回結構的欄位來保存的評估的值 `timer` 引數的 UTC，而不是以本地時間。 每個結構欄位的型別是 `int`, 、，如下所示︰  
  
 `tm_sec`  
 分鐘之後的秒數 \(0 – 59\)。  
  
 `tm_min`  
 小時之後的分鐘 \(0 – 59\)。  
  
 `tm_hour`  
 從午夜開始的小時 \(0 – 23\)。  
  
 `tm_mday`  
 日期的月份 \(1 – 31\)。  
  
 `tm_mon`  
 月 \(0 – 11。1 月 \= 0）。  
  
 `tm_year`  
 年份 （目前年份減去 1900年）。  
  
 `tm_wday`  
 一週天數 \(0\-6;星期日 \= 0）。  
  
 `tm_yday`  
 年中的日 \(0 – 365;1 月 1 \= 0\)。  
  
 `tm_isdst`  
 永遠為 0 的 `gmtime`。  
  
 32 位元和 64 位元版本 `gmtime`, ，`mktime`, ，`mkgmtime`, ，和 `localtime` 都使用常見 `tm` 每個執行緒來進行轉換的結構。 每個呼叫其中一個這些函式會破壞任何先前呼叫的結果。 如果 `timer` 代表的日期是 1970 年 1 月 1 日的午夜之前 `gmtime` 傳回 `NULL`。 不會傳回錯誤。  
  
 `_gmtime64`, 它會使用 `__time64_t` 結構時，請讓總 23:59:59，3000 年 12 月 31 日 UTC，以表示的日期，而 `_gmtime32` 只代表 23:59:59 2038 年 1 月 18 日 UTC 日期。 午夜過後，1970 年 1 月 1 日是這兩個函數的日期範圍的下限。  
  
 `gmtime` 是內嵌函式會評估為 `_gmtime64`, ，和 `time_t` 就相當於 `__time64_t` 除非 `_USE_32BIT_TIME_T` 定義。 如果您必須強制編譯器將解譯 `time_t` 為舊的 32 位元 `time_t`, ，您可以定義 `_USE_32BIT_TIME_T`, ，但是這樣的原因 `gmtime` 是內嵌至 `_gmtime32` 和 `time_t` ，定義為 `__time32_t`。 我們建議，您不要這麼做，因為它不允許在 64 位元平台上，而且在任何情況下，應用程式可能無法在 2038 年 1 月 18 日之後。  
  
 這些函式會驗證它們的參數。 如果 `timer` 是 null 指標，或如果計時器值為負數，這些函式叫用無效參數處理常式中所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回 `NULL` ，並設定 `errno` 到 `EINVAL`。  
  
## 備註  
 `_gmtime32` 函式會細分 `timer` 值，並將它儲存在靜態配置結構的型別 `tm`, ，已定義的時間。H. 值 `timer` 通常取自呼叫 `time` 函式。  
  
> [!NOTE]
>  在大部分情況下，目標環境會嘗試判斷日光節約時間是否生效。 C 執行階段程式庫假設會使用美國的規則實作計算的日光節約時間 \(DST\)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`gmtime`|\<time.h\>|  
|`_gmtime32`|\<time.h\>|  
|`_gmtime64`|\<time.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
  
      // crt_gmtime.c  
// compile with: /W3  
// This program uses _gmtime64 to convert a long-  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm *newtime;  
   __int64 ltime;  
   char buff[80];  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:  
   newtime = _gmtime64( &ltime ); // C4996  
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s  
   asctime_s( buff, sizeof(buff), newtime );  
   printf( "Coordinated universal time is %s\n", buff );  
}  
```  
  
```Output  
國際標準時間是星期二 2 月 12 日 23:11:31 2002年  
```  
  
## .NET Framework 對等用法  
  
-   [System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx)  
  
-   [System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [\_mkgmtime、\_mkgmtime32、\_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)