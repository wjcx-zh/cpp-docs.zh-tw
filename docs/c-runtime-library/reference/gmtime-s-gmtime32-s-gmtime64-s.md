---
title: "gmtime_s、_gmtime32_s、_gmtime64_s | Microsoft Docs"
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
  - "_gmtime32_s"
  - "gmtime_s"
  - "_gmtime64_s"
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
  - "_gmtime_s"
  - "gmtime64_s"
  - "gmtime32_s"
  - "_gmtime64_s"
  - "gmtime_s"
  - "_gmtime32_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "gmtime_s 函式"
  - "gmtime32_s 函式"
  - "時間函式"
  - "gmtime64_s 函式"
  - "_gmtime64_s 函式"
  - "時間結構轉換"
  - "_gmtime_s 函式"
  - "_gmtime32_s 函式"
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gmtime_s、_gmtime32_s、_gmtime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將時間值轉換成結構。 這些是舊版 [\_gmtime32、 \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 中所述的安全性增強 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
errno_t gmtime_s(  
   struct tm* _tm,  
   const __time_t* time  
);  
errno_t _gmtime32_s(  
   struct tm* _tm,  
   const __time32_t* time  
);  
errno_t _gmtime64_s(  
   struct tm* _tm,  
   const __time64_t* time   
);  
```  
  
#### 參數  
 `_tm`  
 指標 `tm` 結構。 傳回結構的欄位來保存的評估的值 `timer` 引數的 UTC，而不是以本地時間。  
  
 `time`  
 指標儲存的時間。 時間表示，如從午夜以來經過的秒 \(00: 00:00\)、 1970 年 1 月 1 日國際標準時間 \(UTC\)。  
  
## 傳回值  
 如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤代碼被定義在 Errno.h;如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-constants.md)。  
  
### 錯誤狀況  
  
|`_tm`|`time`|返回|中的值 `_tm`|  
|-----------|------------|--------|---------------|  
|`NULL`|any|`EINVAL`|不會修改。|  
|不 `NULL` （指向有效的記憶體）|`NULL`|`EINVAL`|所有的欄位設定為\-1。|  
|不 `NULL`|\< 0|`EINVAL`|所有的欄位設定為\-1。|  
  
 在第一次的兩個錯誤條件的情況下無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## 備註  
 `_gmtime32_s` 函式會細分 `time` 值，並將它儲存在型別的結構 `tm`, Time.h 中定義。 結構的位址會傳入 `_tm`。 值 `time` 通常取自呼叫 `time` 函式。  
  
> [!NOTE]
>  目標環境應該試著判斷日光節約時間是否生效。 C 執行階段程式庫假設美國規則實作日光節約時間的計算。  
  
 每個結構欄位的型別是 `int`, ，如下表所示。  
  
 `tm_sec`  
 分鐘之後的秒數 \(0 – 59\)。  
  
 `tm_min`  
 小時之後的分鐘 \(0 – 59\)。  
  
 `tm_hour`  
 從午夜開始的小時 \(0 – 23\)。  
  
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
 永遠為 0 的 `gmtime`。  
  
 `_gmtime64_s`, 它會使用 `__time64_t` 結構，可讓總 23:59:59，3000 年 12 月 31 日 UTC 表示的日期，而 `gmtime32_s` 只代表 23:59:59 2038 年 1 月 18 日 UTC 日期。 午夜過後，1970 年 1 月 1 日是這些函式的日期範圍的下限。  
  
 `gmtime_s` 是內嵌函式評估 `_gmtime64_s` 和 `time_t` 就相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，這將導致 `gmtime_s` 是內嵌至 `_gmtime32_s`。 建議您不要因為您的應用程式可能是在 2038 年 1 月 18 日之後, 會失敗，且不允許在 64 位元平台上。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`gmtime_s`|\<time.h\>|  
|`_gmtime32_s`|\<time.h\>|  
|`_gmtime64_s`|\<time.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_gmtime64_s.c  
// This program uses _gmtime64_s to convert a 64-bit  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime_s to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm newtime;  
   __int64 ltime;  
   char buf[26];  
   errno_t err;  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:   
   err = _gmtime64_s( &newtime, &ltime );  
   if (err)  
   {  
      printf("Invalid Argument to _gmtime64_s.");  
   }  
  
   // Convert to an ASCII representation   
   err = asctime_s(buf, 26, &newtime);  
   if (err)  
   {  
      printf("Invalid Argument to asctime_s.");  
   }  
  
   printf( "Coordinated universal time is %s\n",   
           buf );  
}  
```  
  
```Output  
國際標準時間為星期五 25 年 4 月 20:12:33 2003年  
```  
  
## .NET Framework 對等用法  
  
-   [System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx)  
  
-   [System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [\_mkgmtime、\_mkgmtime32、\_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)