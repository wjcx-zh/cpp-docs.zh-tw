---
title: "localtime_s、_localtime32_s、_localtime64_s | Microsoft Docs"
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
  - "_localtime64_s"
  - "_localtime32_s"
  - "localtime_s"
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
  - "_localtime32_s"
  - "localtime32_s"
  - "localtime_s"
  - "localtime64_s"
  - "_localtime64_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_localtime64_s 函式"
  - "localtime32_s 函式"
  - "_localtime32_s 函式"
  - "localtime64_s 函式"
  - "時間, 轉換值"
  - "localtime_s 函式"
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# localtime_s、_localtime32_s、_localtime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將時間值，轉換和更正當地時區。 這些是舊版 [localtime、 \_localtime32、 \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### 參數  
 `_tm`  
 要填入的時間結構的指標。  
  
 `time`  
 指標的預存的時間。  
  
## 傳回值  
 如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 Errno.h 中定義的錯誤碼。 如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 錯誤狀況  
  
|`_tm`|`time`|傳回值|中的值 `_tm`|叫用無效參數處理常式|  
|-----------|------------|---------|---------------|----------------|  
|`NULL`|any|`EINVAL`|未修改|是|  
|不 `NULL` （指向有效的記憶體）|`NULL`|`EINVAL`|所有的欄位設定為\-1|是|  
|不 `NULL` （指向有效的記憶體）|小於 0 或大於 `_MAX__TIME64_T`|`EINVAL`|所有的欄位設定為\-1|否|  
  
 在第一次的兩個錯誤條件的情況下無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## 備註  
 `_localtime32_s` 函式將儲存為時間轉換 [time\_t](../../c-runtime-library/standard-types.md) 值，並將結果儲存類型的結構 `tm`。`long` 值 `timer` 代表從午夜以來經過的秒 \(00: 00:00\)、 1970 年 1 月 1 日 UTC。 這個值通常取自 `time` 函式。  
  
 `_localtime32_s` 如果使用者第一次設定全域環境變數，更正當地時區 `TZ`。 當 `TZ` 設定，其他三個環境變數 \(`_timezone`, ，`_daylight`, ，和 `_tzname`\) 也會自動設定。 如果 `TZ` 未設定變數， `localtime32_s` 會嘗試使用 \[控制台\] 中的日期\/時間應用程式中指定的時區資訊。 如果無法取得這項資訊，PST8PDT，這表示太平洋時區，使用預設值。 請參閱 [\_tzset](../../c-runtime-library/reference/tzset.md) 這些變數的描述。`TZ` 是 Microsoft 擴充功能並不屬於 ANSI 標準定義的 `localtime`。  
  
> [!NOTE]
>  目標環境應該試著判斷日光節約時間是否生效。  
  
 `_localtime64_s`, 它會使用 `__time64_t` 結構，可讓總 23:59:59，3000 年 12 月 31 日，國際標準時間 \(UTC\) 表示的日期，而 `_localtime32_s` 代表 23:59:59 2038 年 1 月 18 日 UTC 日期。  
  
 `localtime_s` 是內嵌函式評估 `_localtime64_s`, ，和 `time_t` 就相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，這將導致 `localtime_s` 才會評估為 `_localtime32_s`。 建議您不要因為您的應用程式可能是在 2038 年 1 月 18 日之後, 會失敗，且不允許在 64 位元平台上。  
  
 結構類型的欄位 [tm](../../c-runtime-library/standard-types.md) 儲存下列的值，每個都是 `int`。  
  
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
 若日光節約時間已生效; 正值0，如果日光節約時間沒有作用。如果日光節約時間的狀態是未知的負數值。 如果 `TZ` 設定環境變數時，C 執行階段程式庫假設規則適用於美國實作日光節約時間 \(DST\) 的計算。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`localtime_s`|\<time.h\>|  
|`_localtime32_s`|\<time.h\>|  
|`_localtime64_s`|\<time.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## 範例輸出  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## .NET Framework 對等用法  
 [System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)