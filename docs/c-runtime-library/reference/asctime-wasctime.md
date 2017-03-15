---
title: "asctime、_wasctime | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wasctime"
  - "asctime"
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
  - "_tasctime"
  - "asctime"
  - "_wasctime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tasctime 函式"
  - "_wasctime 函式"
  - "asctime 函式"
  - "tasctime 函式"
  - "時間結構轉換"
  - "時間, 轉換"
  - "wasctime 函式"
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# asctime、_wasctime
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換 `tm` 時間結構成字元字串。  這些函式已有更安全的版本可用，請參閱 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
## 語法  
  
```  
char *asctime(   
   const struct tm *timeptr   
);  
wchar_t *_wasctime(   
   const struct tm *timeptr   
);  
```  
  
#### 參數  
 `timeptr`  
 Time\/date 結構。  
  
## 傳回值  
 `asctime` 將指標傳回字串結果; `_wasctime` 指標傳回之寬字元字串結果。  不會回傳錯誤值。  
  
## 備註  
 這些函式已有更安全的版本可用，請參閱  [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
 `asctime` 函式會轉換為結構儲存的時間為字元字串。  `timeptr` 值來自呼叫通常取得到 `gmtime` 或 `localtime`，會將指標傳回 `tm` 結構，定義在 TIME.H。  
  
|timeptr 成員|值|  
|----------------|-------|  
|`tm_hour`|從正夜開始的小時 \(0 – 23\)|  
|`tm_isdst`|如果日光節約時間生效為正數；如果日光節約時間未生效則為0；如果日光節約時間狀態不明則為負數。  C 執行階段程式庫假設使用美國的規則來實作日光節約時間\(DST\)的計算。|  
|`tm_mday`|月份的日期 \(1 – 31\)|  
|`tm_min`|小時 \(以分鐘為單位 \(0 – 59\)\)|  
|`tm_mon`|月份 \(0 – 11；一月 \= 0\)|  
|`tm_sec`|分鐘 \(以秒數為單位 \(0 – 59\)\)|  
|`tm_wday`|星期幾 \(0 – 6；星期日 \= 0\)|  
|`tm_yday`|日期 \(0 – 365；1 月 1 日 \= 0 \)|  
|`tm_year`|年 \(今年年數減去 1900\)|  
  
 要轉換的字元字串也會根據當地時區設定調整。  如需定義時區環境和全域變數的詳細資訊，請參閱 [time](../../c-runtime-library/reference/time-time32-time64.md)、[\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)和[localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函式且 [\_tzset](../../c-runtime-library/reference/tzset.md) 函式會配置於本地時間的相關資訊。  
  
 `asctime` 所產生的結果字串會包含 26 個字元且格式為 `Wed Jan 02 02:03:55 1980\n\0`。  使用 24 小時制。  所有欄位具有相同的寬度。  新行字元和 null 字元佔用字串的前兩個位置。  `asctime` 使用單一，靜態配置緩衝區物件所傳回字串。  對這個函式的呼叫來終結每個呼叫的結果。  
  
 `_wasctime` 是 `asctime`的寬字元版本。  `_wasctime` 和 `asctime` 其餘行為相同。  
  
 這些函式會驗證它們的參數。  如果 `timeptr` 為 null 指標，則為，如果它包含在超出範圍的值，不正確的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，此函式回傳 `NULL` 並設置 `errno` 為 `EINVAL` 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tasctime`|`asctime`|`asctime`|`_wasctime`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`asctime`|\<time.h\>|  
|`_wasctime`|\<time.h\> or \<wchar.h\>|  
  
## 範例  
 這個程式以長整數 `aclock` 存放系統時間，使用 `asctime` 函式，將它轉譯成結構 `newtime` 然後轉換成輸出的字串形式。  
  
```  
// crt_asctime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
    struct tm   *newTime;  
    time_t      szClock;  
  
    // Get time in seconds  
    time( &szClock );  
  
    // Convert time to struct tm form   
    newTime = localtime( &szClock );  
  
    // Print local time as a string.  
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996  
    // Note: asctime is deprecated; consider using asctime_s instead  
}  
```  
  
  **目前的日期和時間: 2002年 2 月 03 日星期日 11:38: 58**    
## .NET Framework 對等用法  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)