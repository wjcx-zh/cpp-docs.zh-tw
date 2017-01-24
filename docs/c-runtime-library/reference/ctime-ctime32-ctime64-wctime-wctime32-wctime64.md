---
title: "ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64 | Microsoft Docs"
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
  - "_ctime64"
  - "_wctime32"
  - "ctime"
  - "_wctime64"
  - "_ctime32"
  - "_wctime"
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
  - "_wctime64"
  - "_ctime32"
  - "_tctime"
  - "_wctime"
  - "_wctime32"
  - "_tctime64"
  - "_ctime64"
  - "ctime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tctime64 函式"
  - "_ctime32 函式"
  - "ctime32 函式"
  - "_wctime 函式"
  - "wctime64 函式"
  - "_tctime64 函式"
  - "_tctime32 函式"
  - "_ctime64 函式"
  - "_wctime64 函式"
  - "ctime 函式"
  - "wctime32 函式"
  - "ctime64 函式"
  - "_wctime32 函式"
  - "_tctime 函式"
  - "tctime32 函式"
  - "tctime 函式"
  - "wctime 函式"
  - "時間，轉換"
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將時間值轉換為字串，並調整的本地時間區域設定。 更安全的版本，這些函式可供使用。請參閱 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)。  
  
## 語法  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### 參數  
 `timer`  
 指標儲存的時間。  
  
## 傳回值  
 產生的字元字串指標。`NULL` 如果就會傳回︰  
  
-   `time` 代表之前 1970 年 1 月 1 日的午夜 UTC 日期。  
  
-   如果您使用 `_ctime32` 或 `_wctime32` 和 `time` 代表 23:59:59 2038 年 1 月 18 日 UTC 之後的日期。  
  
-   如果您使用 `_ctime64` 或 `_wctime64` 和 `time` 代表 23:59:59，3000 年 12 月 31 日 UTC 之後的日期。  
  
 `ctime` 是內嵌函式評估 `_ctime64` 和 `time_t` 就相當於 `__time64_t`。 如果您要強制編譯器將解譯 `time_t` 為舊的 32 位元 `time_t`, ，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，這將導致 `ctime` 才會評估為 `_ctime32`。 建議您不要因為您的應用程式可能是在 2038 年 1 月 18 日之後, 會失敗，且不允許在 64 位元平台上。  
  
## 備註  
 `ctime` 函式將儲存為時間值，轉換 [time\_t](../../c-runtime-library/standard-types.md) 轉換為字元字串的值。`timer` 值通常取自呼叫 [時間](../../c-runtime-library/reference/time-time32-time64.md), ，傳回午夜起經過的秒數 \(00: 00:00\)、 1970 年 1 月 1 日國際標準時間 \(UTC\)。 傳回值的字串包含完全 26 個字元，且具有下列形式︰  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 會使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 \('\\n'\) 和 null 字元 \('\\0'\) 所佔用的最後兩個字串的位置。  
  
 已轉換的字元字串也會根據本地時間區域設定調整。 請參閱 `time`, ，[\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), ，和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函式，如需設定當地時間和 [\_tzset](../../c-runtime-library/reference/tzset.md) 函式定義的時區環境和全域變數的相關詳細資料。  
  
 呼叫 `ctime` 修改所使用的單一靜態配置的緩衝區 `gmtime` 和 `localtime` 函式。 每個呼叫其中一個這些常式會終結先前呼叫的結果。`ctime` 共用與靜態緩衝區 `asctime` 函式。 因此，呼叫 `ctime` 終結任何先前呼叫的結果 `asctime`, ，`localtime`, ，或 `gmtime`。  
  
 `_wctime` 和 `_wctime64` 是寬字元版本 `ctime` 和 `_ctime64`; 傳回寬字元字串的指標。 否則， `_ctime64`, ，`_wctime`, ，和 `_wctime64` 的行為和 `ctime`。  
  
 這些函式會驗證它們的參數。 如果 `timer` 是 null 指標，或如果計時器值為負數，這些函式叫用無效參數處理常式中所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，函式會傳回 `NULL` ，並設定 `errno` 到 `EINVAL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`ctime`|\<time.h\>|  
|`_ctime32`|\<time.h\>|  
|`_ctime64`|\<time.h\>|  
|`_wctime`|\<.h \> 或 \< wchar.h \>|  
|`_wctime32`|\<.h \> 或 \< wchar.h \>|  
|`_wctime64`|\<.h \> 或 \< wchar.h \>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
時間是星期三年 2 月 13 日 16:04:43 2002年  
```  
  
## .NET Framework 對等用法  
  
-   [System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)