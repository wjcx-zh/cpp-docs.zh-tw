---
title: "_strtime_s、_wstrtime_s | Microsoft Docs"
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
  - "_wstrtime_s"
  - "_strtime_s"
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
  - "_wstrtime_s"
  - "strtime_s"
  - "wstrtime_s"
  - "_strtime_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtime_s 函式"
  - "_wstrtime_s 函式"
  - "將時間複製到緩衝區"
  - "strtime_s 函式"
  - "時間, 複製"
  - "wstrtime_s 函式"
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtime_s、_wstrtime_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製目前時間到緩衝區。  這些是 [\_strtime, \_wstrtime](../../c-runtime-library/reference/strtime-wstrtime.md)的安全性增強版本，如[CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 語法  
  
```  
errno_t _strtime_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrtime_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strtime_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrtime_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### 參數  
 \[out\] `buffer`  
 長度至少 10 個位元組，會將寫時間入的緩衝區。  
  
 \[in\] `numberOfElements`  
 緩衝區的大小。  
  
## 傳回值  
 如果成功，則為零。  
  
 如果錯誤情況發生， 則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果發生失敗，則傳回值為錯誤碼。  錯誤碼在ERRNO.H 中定義;這個函式會產生的錯誤請參閱下表。  如需和錯誤碼的詳細資訊，請參閱[errno 常數](../../c-runtime-library/errno-constants.md) 。  
  
### 錯誤狀況  
  
|`buffer`|`numberOfElements`|傳回|`buffer` 的內容|  
|--------------|------------------------|--------|------------------|  
|`NULL`|任何。|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的緩衝區\)|0|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的緩衝區\)|0 \< size \< 9|`EINVAL`|空字串|  
|不是 `NULL` \(指向有效的緩衝區\)|Size \> 9|0|在圖例中指定格式化的目前時間|  
  
## 安全性問題  
 如果`numberOfElements`參數大於9，則傳入一個無效非NULL值造成存取違規。  
  
 傳遞大於緩衝區實際大小的值給`numberOfElements`會導致緩衝區滿溢。  
  
## 備註  
 這些函式提供 `_strtime` 和 `_wstrtime`更安全的版本。  `_strtime_s` 函式複製目前本地時間到緩衝區所指向的 `timestr`*。*時間會格式化為 `hh:mm:ss`，其中`hh` 是表示 24 小時制附註的二位數小時的，`mm`是代表透過小時的兩位數的分鐘，`ss` 是表示秒數的兩個數字。  例如， `18:23:44` 字串表示下午 6 點 23 分 44 秒。緩衝區的長度必須至少是 9 個位元組；實際大小則由第二個參數指定。  
  
 `_wstrtime` 是 `_strtime` 的寬字元版本，`_wstrtime` 函式的參數和回傳值是寬字元字串。  這三個函式其餘部分的運作相同。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應：  
  
|TCHAR.H 常式|\_UNICODE &\_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|---------------------------|----------------|-------------------|  
|`_tstrtime_s`|`_strtime_s`|`_strtime_s`|`_wstrtime_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strtime_s`|\<time.h\>|  
|`_wstrtime_s`|\<time.h\> or \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// strtime_s.c  
  
#include <time.h>  
#include <stdio.h>  
  
int main()  
{  
    char tmpbuf[9];  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    err = _strtime_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
      exit(1);  
    }  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    err = _strdate_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
}  
```  
  
  **OS time:            14:37:49**  
**OS date:            04\/25\/03**   
## .NET Framework 對等用法  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)