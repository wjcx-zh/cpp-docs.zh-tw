---
title: "ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ctime64_s"
  - "_wctime32_s"
  - "ctime_s"
  - "_wctime64_s"
  - "_ctime32_s"
  - "_wctime_s"
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
  - "ctime64_s"
  - "_ctime32_s"
  - "_tctime32_s"
  - "_ctime64_s"
  - "_wctime_s"
  - "_tctime_s"
  - "_tctime64_s"
  - "ctime_s"
  - "ctime32_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wctime32_s 函式"
  - "ctime64_s 函式"
  - "_tctime64_s 函式"
  - "_wctime_s 函式"
  - "tctime_s 函式"
  - "_wctime64_s 函式"
  - "ctime_s 函式"
  - "ctime32_s 函式"
  - "_ctime64_s 函式"
  - "tctime64_s 函式"
  - "wctime64_s 函式"
  - "wctime_s 函式"
  - "_tctime_s 函式"
  - "tctime32_s 函式"
  - "wctime32_s 函式"
  - "時間, 轉換"
  - "_ctime32_s 函式"
  - "_tctime32_s 函式"
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將時間值轉換為字串，並調整的本地時間區域設定。 這些是舊版 [ctime、 \_ctime64、 \_wctime、 \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t ctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _ctime32_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _ctime64_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time64_t *time )  
;  
errno_t _wctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _wctime32_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _wctime64_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time64_t *time   
);  
template <size_t size>  
errno_t _ctime32_s(   
   char (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _ctime64_s(   
   char (&buffer)[size],  
   const __time64_t *time  
); // C++ only  
template <size_t size>  
errno_t _wctime32_s(   
   wchar_t (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _wctime64_s(   
   wchar_t (&buffer)[size],  
   const __time64_t *time   
); // C++ only  
```  
  
#### 參數  
 \[\] out `buffer`  
 必須足以容納 26 個字元。 字元字串結果時，指標或 `NULL`如果︰  
  
-   `time` 代表之前 1970 年 1 月 1 日的午夜 UTC 日期。  
  
-   如果您使用 `_ctime32_s` 或 `_wctime32_s` 和 `time` 代表 23:59:59 2038 年 1 月 18 日 UTC 之後的日期。  
  
-   如果您使用 `_ctime64_s` 或 `_wctime64_s` 和 `time` 代表 23:59:59，3000 年 12 月 31 日 UTC 之後的日期。  
  
-   如果您使用 `_ctime_s` 或 `_wctime_s`, ，這些函式是包裝函式以先前的函式。 請參閱＜備註＞一節。  
  
 \[in\] `numberOfElements`  
 緩衝區的大小。  
  
 \[\] t in`ime`  
 指標儲存的時間。  
  
## 傳回值  
 如果成功，則為零。 如果有失敗，因為不正確的參數無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則會傳回錯誤碼。 ERRNO 中定義的錯誤碼。H。如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-constants.md)。 下表中，會顯示每個錯誤狀況的擲回的實際錯誤碼。  
  
## 錯誤狀況  
  
|`buffer`|`numberOfElements`|`time`|返回|中的值 `buffer`|  
|--------------|------------------------|------------|--------|------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|不 `NULL` （指向有效的記憶體）|0|any|`EINVAL`|未修改|  
|不 `NULL`|0 \< \< 26 調整大小|any|`EINVAL`|空字串|  
|不 `NULL`|\>\= 26|NULL|`EINVAL`|空字串|  
|不 `NULL`|\>\= 26|\< 0|`EINVAL`|空字串|  
  
## 備註  
 `ctime_s` 函式將儲存為時間值，轉換 [time\_t](../../c-runtime-library/standard-types.md) 結構轉換為字元字串。`time` 值通常取自呼叫 [時間](../../c-runtime-library/reference/time-time32-time64.md), ，傳回午夜起經過的秒數 \(00: 00:00\)、 1970 年 1 月 1 日國際標準時間 \(UTC\)。 傳回值的字串包含完全 26 個字元，且具有下列形式︰  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 會使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 \('\\n'\) 和 null 字元 \('\\0'\) 所佔用的最後兩個字串的位置。  
  
 已轉換的字元字串也會根據本地時間區域設定調整。 請參閱 `time`, ，[\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), ，和 [localtime32\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函式，如需設定當地時間和 [\_tzset](../../c-runtime-library/reference/tzset.md) 函式定義的時區環境和全域變數的相關資訊。  
  
 `_wctime32_s` 和 `_wctime64_s` 是寬字元版本 `_ctime32_s` 和 `_ctime64_s`; 傳回寬字元字串的指標。 否則， `_ctime64_s`, ，`_wctime32_s`, ，和 `_wctime64_s` 的行為和 `_ctime32_s`。  
  
 `ctime_s` 是內嵌函式會評估為 `_ctime64_s` 和 `time_t` 就相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，這將導致 `ctime_s` 才會評估為 `_ctime32_s`。 建議您不要因為您的應用程式可能是在 2038 年 1 月 18 日之後, 會失敗，且不允許在 64 位元平台上。  
  
 C \+ \+ 中使用這些函式簡化了範本多載。多載可自動推斷緩衝區長度，因而不須指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tctime_s`|`ctime_s`|`ctime_s`|`_wctime_s`|  
|`_tctime32_s`|`_ctime32_s`|`_ctime32_s`|`_wctime32_s`|  
|`_tctime64_s`|`_ctime64_s`|`_ctime64_s`|`_wctime64_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`ctime_s,`<br /><br /> `_ctime32_s,`<br /><br /> `_ctime64_s`|\<time.h\>|  
|`_wctime_s,`<br /><br /> `_wctime32_s,`<br /><br /> `_wctime64_s`|\<.h \> 或 \< wchar.h \>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## 範例  
  
```  
// crt_wctime_s.c  
/* This program gets the current  
 * time in time_t form and then uses _wctime_s to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
#define SIZE 26  
  
int main( void )  
{  
   time_t ltime;  
   wchar_t buf[SIZE];  
   errno_t err;  
  
   time( &ltime );  
  
   err = _wctime_s( buf, SIZE, &ltime );  
   if (err != 0)  
   {  
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);  
   }  
   wprintf_s( L"The time is %s\n", buf );  
}  
```  
  
## 範例輸出  
  
```  
The time is Fri Apr 25 13:03:39 2003  
```  
  
## .NET Framework 對等用法  
  
-   [System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)