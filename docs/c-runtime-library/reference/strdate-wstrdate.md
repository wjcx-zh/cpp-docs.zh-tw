---
title: "_strdate、_wstrdate | Microsoft Docs"
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
  - "_strdate"
  - "_wstrdate"
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
  - "_tstrdate"
  - "wstrdate"
  - "_wstrdate"
  - "_strdate"
  - "strdate"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "strdate 函式"
  - "日期，複製"
  - "tstrdate 函式"
  - "_wstrdate 函式"
  - "wstrdate 函式"
  - "_strdate 函式"
  - "_tstrdate 函式"
  - "複製日期"
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdate、_wstrdate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製目前系統日期至緩衝區。  這些函式已有更安全的版本可用，請參閱 [\_strdate\_s、\_wstrdate\_s](../../c-runtime-library/reference/strdate-s-wstrdate-s.md)。  
  
## 語法  
  
```  
char *_strdate(  
   char *datestr   
);  
wchar_t *_wstrdate(  
   wchar_t *datestr   
);  
template <size_t size>  
char *_strdate(  
   char (&datestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrdate(  
   wchar_t (&datestr)[size]  
); // C++ only  
```  
  
#### 參數  
 `datestr`  
 指向包含格式的日期字串緩衝區的指標。  
  
## 傳回值  
 每一個這些函式都會傳回結果字元字串 `datestr` 的指標。  
  
## 備註  
 這些函式已有更安全的版本可用，請參閱 [\_strdate\_s, \_wstrdate\_s](../../c-runtime-library/reference/strdate-s-wstrdate-s.md)。  建議在可能的情況下使用更安全的函式。  
  
 `_strdate` 函式複製目前系統日期至由 `datestr` 指向的緩衝區，格式是 `mm`\/`dd`\/`yy`，其中 `mm` 是代表月份的兩位數， `dd` 是表示日期的兩位數，且 `yy` 年的後兩位數。  例如， `12/05/99` 字串表示 1999 年 12 月 5 日。  緩衝區的長度必須至少是 9 個位元組。  
  
 如果 `datestr` 為 `NULL` 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 \-1 並將`errno` 設定為 `EINVAL`。  
  
 `_wstrdate` 是 `_strdate` 的寬字元版本，`_wstrdate` 函式的參數和回傳值是寬字元字串。  這三個函式其餘部分的運作相同。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE 和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstrdate`|`_strdate`|`_strdate`|`_wstrdate`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strdate`|\<time.h\>|  
|`_wstrdate`|\<time.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// strdate.c  
// compile with: /W3  
#include <time.h>  
#include <stdio.h>  
int main()  
{  
    char tmpbuf[9];  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996  
    // Note: _strdate is deprecated; consider using _strdate_s instead  
}  
```  
  
  **OS 日期: 04\/25\/03**   
## .NET Framework 對等用法  
 [System::DateTime::Parse](https://msdn.microsoft.com/en-us/library/system.datetime.parse.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)