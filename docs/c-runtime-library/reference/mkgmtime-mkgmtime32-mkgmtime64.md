---
title: "_mkgmtime、_mkgmtime32、_mkgmtime64 | Microsoft Docs"
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
  - "_mkgmtime32"
  - "_mkgmtime64"
  - "_mkgmtime"
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
  - "_mkgmtime64"
  - "mkgmtime32"
  - "_mkgmtime32"
  - "mkgmtime"
  - "mkgmtime64"
  - "_mkgmtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mkgmtime32 函式"
  - "時間函式"
  - "mkgmtime 函式"
  - "_mkgmtime 函式"
  - "轉換時間"
  - "mkgmtime64 函式"
  - "_mkgmtime64 函式"
  - "_mkgmtime32 函式"
  - "時間, 轉換"
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mkgmtime、_mkgmtime32、_mkgmtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將所表示的 UTC 時間轉換 `tm``struct` 為 UTC 時間表示的 `time_t` 型別。  
  
## 語法  
  
```  
  
time_t _mkgmtime(  
   struct tm*   
timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm*   
timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm*   
timeptr  
);  
  
```  
  
#### 參數  
 `timeptr`  
 UTC 時間，做為指標 `struct``tm` 轉換。  
  
## 傳回值  
 型別數量 `__time32_t` 或 `__time64_t` 代表秒數過自 1970 年 1 月 1 日，以國際標準時間 \(UTC\)。 如果日期超出範圍 （請參閱 \< 備註 \> 一節） 或輸入無法解譯為有效的時間，傳回值為\-1。  
  
## 備註  
 `_mkgmtime32` 和 `_mkgmtime64` 函數會將轉換為 UTC 時間，以 `__time32_t` 或 `__time64_t` 型別，表示的 UTC 時間。 若要將當地時間轉換成 UTC 時間，使用 `mktime`, ，`_mktime32`, ，和 `_mktime64` 改。  
  
 `_mkgmtime` 是內嵌函式會評估為 `_mkgmtime64`, ，和 `time_t` 就相當於 `__time64_t`。 如果您要強制編譯器將解譯 `time_t`為舊的 32 位元 `time_t`, ，您可以定義 `_USE_32BIT_TIME_T`。 建議您不要因為您的應用程式可能會失敗之後 2038 年 1 月 18 日 \(32 位元的最大範圍 `time_t`\)，且不允許在 64 位元平台上。  
  
 結構中所傳遞的時間將會變更，如下所示，相同的方式是變更與 `_mktime` 函式︰ `tm_wday` 和 `tm_yday` 欄位會設定為根據的值的新值 `tm_mday` 和 `tm_year`。 當指定 `tm` 結構時間時，請將 `tm_isdst` 欄位設定為：  
  
-   零 \(0\)，以指出標準時間已生效。  
  
-   大於 0 的值，以指出日光節約時間已生效。  
  
-   小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。  
  
 C 執行階段程式庫會使用 TZ 環境變數來決定正確的日光節約時間。 如果未設定 TZ，作業系統會查詢以取得正確的地區日光節約時間行為。`tm_isdst` 是必要的欄位。 如果未設定，未定義其值和傳回值，從 `mktime` 我們無法預測。  
  
 範圍 `_mkgmtime32` 函式是從 1970 年 1 月 1 日午夜 UTC 到 23:59:59 2038 年 1 月 18 日 UTC。 範圍 `_mkgmtime64` 是從 1970 年 1 月 1 日午夜 UTC 到 23:59:59，3000 年 12 月 31 日 UTC。 範圍外的日期會導致傳回值為\-1。 範圍 `_mkgmtime` 取決於是否 `_USE_32BIT_TIME_T` 定義。 如果未定義 （預設值） 的範圍是屬於 `_mkgmtime64`; 否則範圍僅限於的 32 位元範圍 `_mkgmtime32`。  
  
 請注意， `gmtime` 和 `localtime` 使用單一靜態配置的緩衝區來進行轉換。 如果您提供此緩衝區 `mkgmtime`, ，先前的內容將被終結。  
  
## 範例  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## 範例輸出  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 下列範例顯示如何使用計算的星期和年份的日期值填寫不完整的結構。  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## 輸出  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)