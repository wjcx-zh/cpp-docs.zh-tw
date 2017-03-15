---
title: "_strdate_s、_wstrdate_s | Microsoft Docs"
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
  - "_strdate_s"
  - "_wstrdate_s"
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
  - "_strdate_s"
  - "wstrdate_s"
  - "_wstrdate_s"
  - "strdate_s"
  - "_tstrdate_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "日期，複製"
  - "tstrdate_s 函式"
  - "wstrdate_s 函式"
  - "_tstrdate_s 函式"
  - "strdate_s 函式"
  - "複製日期"
  - "_strdate_s 函式"
  - "_wstrdate_s 函式"
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdate_s、_wstrdate_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製目前系統日期至緩衝區。  這些是 [\_strdate, \_wstrdate](../../c-runtime-library/reference/strdate-wstrdate.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _strdate_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrdate_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strdate_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrdate_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### 參數  
 \[out\] `buffer`  
 將套用格式的日期字串填入的緩衝區的指標。  
  
 \[in\] `numberOfElements`  
 緩衝區的大小。  
  
## 傳回值  
 如果成功，則為零。  如果發生失敗，則傳回值為錯誤碼。  錯誤碼在ERRNO.H 中定義;這個函式會產生的錯誤請參閱下表。  如需錯誤碼的詳細資訊，請參閱 [errno](../../c-runtime-library/errno-constants.md)。  
  
## 錯誤狀況  
  
|`buffer`|`numberOfElements`|傳回|`buffer` 的內容|  
|--------------|------------------------|--------|------------------|  
|`NULL`|任何。|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的緩衝區\)|0|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的緩衝區\)|0 \< `numberOfElements` \< 9|`EINVAL`|空字串|  
|不是 `NULL` \(指向有效的緩衝區\)|`numberOfElements` \>\= 9|0|在圖例中指定格式化的目前日期|  
  
## 安全性問題  
 如果 `numberOfElements` 參數大於 9.，傳入緩衝區無效非 `NULL` 值造成存取違規。  
  
 透過大於 `buffer` 的實際大小的值會導致緩衝區滿溢。  
  
## 備註  
 這些函式提供 `_strdate` 和 `_wstrdate`更安全的版本。  `_strdate_s` 函式複製目前系統日期至由 `buffer` 指向的緩衝區，格式是 `mm`\/`dd`\/`yy`，其中 `mm` 是代表月份的兩位數， `dd` 是表示日期的兩位數，且 `yy` 年的後兩位數。  例如， `12/05/99` 字串表示 1999 年 12 月 5 日。  緩衝區的長度必須至少是 9 個字元。  
  
 `_wstrdate_s` 是 `_strdate_s` 的寬字元版本，`_wstrdate_s` 函式的參數和回傳值是寬字元字串。  這三個函式其餘部分的運作相同。  
  
 如果 `buffer` 是 `NULL` 指標，或者如果 `numberOfElements` 小於 9 個字元，無效的參數呼叫處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續執行，這些函式傳回 \-1 並將 `errno` 設為 `EINVAL` ，如果緩衝區是 `NULL` ，或 `numberOfElements` 小於或等於 0，則將 `errno` 設為 `ERANGE` ，如果 `numberOfElements` 小於 9。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應：  
  
|TCHAR.H 常式|\_UNICODE &和 \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strdate`|\<time.h\>|  
|`_wstrdate`|\<time.h\> or \<wchar.h\>|  
|`_strdate_s`|\<time.h\>|  
  
## 範例  
 請參閱 [time](../../c-runtime-library/reference/time-time32-time64.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::DateTime::Parse](https://msdn.microsoft.com/en-us/library/system.datetime.parse.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)