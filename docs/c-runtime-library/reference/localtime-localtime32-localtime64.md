---
title: "localtime，_localtime32，_localtime64 | Microsoft Docs"
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
  - "_localtime64"
  - "_localtime32"
  - "localtime"
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
  - "localtime64"
  - "_localtime64"
  - "localtime32"
  - "localtime"
  - "_localtime32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "localtime32 函式"
  - "_localtime32 函式"
  - "_localtime64 函式"
  - "localtime64 函式"
  - "localtime 函式"
  - "時間，轉換值"
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# localtime，_localtime32，_localtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換時間值，並更正當地時區。 更安全的版本，這些函式可供使用。請參閱 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)。  
  
## 語法  
  
```  
struct tm *localtime(  
   const time_t *timer   
);  
struct tm *_localtime32(  
   const __time32_t *timer  
);  
struct tm *_localtime64(  
   const __time64_t *timer   
);  
```  
  
#### 參數  
 `timer`  
 指標儲存的時間。  
  
## 傳回值  
 將指標傳回結構的結果，或 `NULL` 如果傳遞給函數的日期︰  
  
-   自 1970 年 1 月 1 日午夜之前  
  
-   03:14:07，是在 2038 年 1 月 19 日，UTC 之後 \(使用 `_time32` 和 `time32_t`\)。  
  
-   23:59:59，3000 年 12 月 31 日 UTC 之後 \(使用 `_time64` 和 `__time64_t`\)。  
  
 `_localtime64`, 它會使用 `__time64_t` 結構，可讓總 23:59:59，3000 年 12 月 31 日，國際標準時間 \(UTC\) 表示的日期，而 `_localtime32` 代表 23:59:59 2038 年 1 月 18 日 UTC 日期。  
  
 `localtime` 是內嵌函式評估 `_localtime64`, ，和 `time_t` 就相當於 `__time64_t`。 如果您要強制編譯器將解譯 `time_t`為舊的 32 位元 `time_t`, ，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，這將導致 `localtime` 才會評估為 `_localtime32`。 建議您不要因為您的應用程式可能是在 2038 年 1 月 18 日之後, 會失敗，且不允許在 64 位元平台上。  
  
 結構類型的欄位 [tm](../../c-runtime-library/standard-types.md) 儲存下列的值，每個都是 `int`:  
  
 `tm_sec`  
 分鐘之後的秒數 \(0 – 59\)。  
  
 `tm_min`  
 小時之後的分鐘 \(0 – 59\)。  
  
 `tm_hour`  
 午夜之後的小時 \(0 – 23\)。  
  
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
 若日光節約時間已生效; 正值0，如果日光節約時間沒有作用。如果日光節約時間的狀態是未知的負數值。 如果 `TZ` 設定環境變數時，C 執行階段程式庫假設規則適用於美國實作日光節約時間 \(DST\) 計算。  
  
## 備註  
 `localtime` 函式將儲存為時間轉換 [time\_t](../../c-runtime-library/standard-types.md) 值，並將結果儲存類型的結構 `tm`。`long` 值 `timer` 代表從午夜以來經過的秒 \(00: 00:00\)、 1970 年 1 月 1 日 UTC。 這個值通常取自 `time` 函式。  
  
 32 位元和 64 位元版本 `gmtime`, ，`mktime`, ，`mkgmtime`, ，和 `localtime` 所有使用單一 `tm` 每個執行緒來進行轉換的結構。 每個呼叫其中一個這些常式會終結先前呼叫的結果。  
  
 `localtime` 如果使用者第一次設定全域環境變數更正當地時區 `TZ`。 當 `TZ` 設定，其他三個環境變數 \(`_timezone`, ，`_daylight`, ，和 `_tzname`\) 也會自動設定。 如果 `TZ` 未設定變數， `localtime` 會嘗試使用 \[控制台\] 中的日期\/時間應用程式中指定的時區資訊。 如果無法取得這項資訊，PST8PDT，這表示太平洋時區，使用預設值。 請參閱 [\_tzset](../../c-runtime-library/reference/tzset.md) 這些變數的描述。`TZ` 是 Microsoft 擴充功能並不屬於 ANSI 標準定義的 `localtime`。  
  
> [!NOTE]
>  目標環境應該試著判斷日光節約時間是否生效。  
  
 這些函式會驗證它們的參數。 如果 `timer` 是 null 指標，或如果計時器值為負數，這些函式叫用無效參數處理常式中所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回 `NULL` ，並設定 `errno` 到 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`localtime`|\<time.h\>|  
|`_localtime32`|\<time.h\>|  
|`_localtime64`|\<time.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_localtime.cpp  
// compile with: /W3  
/* This program uses _time64 to get the current time   
 * and then uses localtime64() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm *newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
  
        _time64( &long_time );           // Get time as 64-bit integer.  
                                         // Convert to local time.  
        newtime = _localtime64( &long_time ); // C4996  
        // Note: _localtime64 deprecated; consider _localetime64_s  
  
        if( newtime->tm_hour > 12 )        // Set up extension.  
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime->tm_hour > 12 )        // Convert from 24-hour  
                newtime->tm_hour -= 12;    //   to 12-hour clock.  
        if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime->tm_hour = 12;  
  
        char buff[30];  
        asctime_s( buff, sizeof(buff), newtime );  
        printf( "%.19s %s\n", buff, am_pm );  
}  
```  
  
```Output  
星期二年 2 月 12 上午 10:05:58  
```  
  
## .NET Framework 對等用法  
 [System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)