---
title: "_strtime、_wstrtime | Microsoft Docs"
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
  - "_wstrtime"
  - "_strtime"
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
  - "_wstrtime"
  - "_strtime"
  - "wstrtime"
  - "strtime"
  - "_tstrtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtime 函式"
  - "_tstrtime 函式"
  - "_wstrtime 函式"
  - "將時間複製到緩衝區"
  - "strtime 函式"
  - "時間, 複製"
  - "tstrtime 函式"
  - "wstrtime 函式"
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtime、_wstrtime
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製時間到緩衝區。  這些函式已有更安全的版本可用，請參閱 [\_strtime\_s、\_wstrtime\_s](../../c-runtime-library/reference/strtime-s-wstrtime-s.md)。  
  
## 語法  
  
```  
char *_strtime(  
   char *timestr   
);  
wchar_t *_wstrtime(  
   wchar_t *timestr   
);  
template <size_t size>  
char *_strtime(  
   char (&timestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrtime(  
   wchar_t (&timestr)[size]  
); // C++ only  
```  
  
#### 參數  
 `timestr`  
 時間字串  
  
## 傳回值  
 傳回結果字元字串`timestr`的指標。  
  
## 備註  
 `_strtime` 函式複製目前本地時間到緩衝區所指向的 `timestr`*。*時間會格式化為 `hh:mm:ss`，其中`hh` 是表示 24 小時制附註的二位數小時的，`mm`是代表透過小時的兩位數的分鐘，`ss` 是表示秒數的兩個數字。  例如， `18:23:44` 字串表示下午 6 點 23 分 44 秒。緩衝區的長度必須至少是 9 個位元組。  
  
 `_wstrtime` 是 `_strtime` 的寬字元版本，`_wstrtime` 函式的參數和回傳值是寬字元字串。  這些函式另有相同的行為。如果 `timestr` 是 `NULL` 指標，或 `timestr` 的格式不正確，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果例外狀況允許繼續執行，這些函式會傳回 NULL 並將 `errno` 設為 `EINVAL` ，如果 `timestr` 為 null 或將 `errno` 設為 `ERANGE` ，如果 `timestr` 格式不正確。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE &\_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|---------------------------|----------------|-------------------|  
|`_tstrtime`|`_strtime`|`_strtime`|`_wstrtime`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strtime`|\<time.h\>|  
|`_wstrtime`|\<time.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strtime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char tbuffer [9];  
   _strtime( tbuffer ); // C4996  
   // Note: _strtime is deprecated; consider using _strtime_s instead  
   printf( "The current time is %s \n", tbuffer );  
}  
```  
  
  **目前時間是 14:21:44。**   
## .NET Framework 對等用法  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)