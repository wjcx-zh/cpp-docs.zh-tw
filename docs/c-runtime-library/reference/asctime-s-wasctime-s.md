---
title: "asctime_s、_wasctime_s | Microsoft Docs"
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
  - "_wasctime_s"
  - "asctime_s"
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
  - "asctime_s"
  - "_wasctime_s"
  - "_tasctime_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tasctime_s 函式"
  - "_wasctime_s 函式"
  - "asctime_s 函式"
  - "tasctime_s 函式"
  - "時間結構轉換"
  - "時間, 轉換"
  - "wasctime_s 函式"
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# asctime_s、_wasctime_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換 `tm` 時間結構成字元字串。  這些是 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述。  
  
## 語法  
  
```  
errno_t asctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const struct tm *_tm   
);  
errno_t _wasctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements  
   const struct tm *_tm   
);  
template <size_t size>  
errno_t asctime_s(   
   char (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
template <size_t size>  
errno_t _wasctime_s(   
   wchar_t (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
```  
  
#### 參數  
 `buffer`  
 \[out\] 儲存結果字串之緩衝區的指標。  這個函式採用指標到具有 `numberOfElements`指定大小的有效的記憶體位置。  
  
 `numberOfElements`  
 \[in\] 用來儲存結果的緩衝區大小。  
  
 `_tm`  
 \[in\] Time\/date 結構  這個函式採用指標到有效的 `struct` `tm` 物件。  
  
## 傳回值  
 如果成功，則為零。  如果有失敗，就會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續執行，則傳回值為錯誤碼。  錯誤碼在 ERRNO.H 中定義。  如需詳細資訊，請參閱[errno 常數](../../c-runtime-library/errno-constants.md)。  為每個錯誤條件傳回的實際錯誤碼如下表中所示。  
  
### 錯誤狀況  
  
|`buffer`|`numberOfElements`|`tm`|傳回|在 `buffer` 的值|  
|--------------|------------------------|----------|--------|-------------------|  
|`NULL`|Any|Any|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的記憶體\)|0|Any|`EINVAL`|未修改|  
|非`NULL`|0\< size \< 26|Any|`EINVAL`|空字串|  
|非`NULL`|\>\= 26|`NULL`|`EINVAL`|空字串|  
|非`NULL`|\>\= 26|無效的時間結構或超出時間元件的範圍值|`EINVAL`|空字串|  
  
> [!NOTE]
>  `wasctime_s` 的錯誤狀況類似於 `asctime_s` ，除了大小限制在文字測量。  
  
## 備註  
 `asctime` 函式會轉換為結構儲存的時間為字元字串。  `_tm` 值通常取得來自對 `gmtime` 或 `localtime` 的呼叫。  兩個函式可用來填入 `tm` 結構，如 TIME.H. 定義。  
  
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
  
 要轉換的字元字串也會根據當地時區設定調整。  請參閱 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md), [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)，如需配置本地時間的詳細資訊請參閱 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函式，而定義時區環境和全域變數的詳細資訊請參閱 [\_tzset](../../c-runtime-library/reference/tzset.md) 函式。  
  
 `asctime_s` 所產生的結果字串會包含 26 個字元且格式為 `Wed Jan 02 02:03:55 1980\n\0`。  使用 24 小時制。  所有欄位具有相同的寬度。  新行字元和 null 字元佔用字串的前兩個位置。  做為第二個參數傳遞的值至少在這必須這麼大。  如果較少，將會傳回錯誤碼 `EINVAL`。  
  
 `_wasctime_s` 是 `asctime_s`的寬字元版本。  `_wasctime_s` 和 `asctime_s` 其餘行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tasctime_s`|`asctime_s`|`asctime_s`|`_wasctime_s`|  
  
 在 C\+\+ 中，這些函式的使用被簡化為使用樣板多載；使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`asctime_s`|\<time.h\>|  
|`_wasctime_s`|\<time.h\> or \<wchar.h\>|  
  
## 安全性  
 如果緩衝區指標不是 `NULL` ，而且指標未指向有效的緩衝區，函式會覆寫所在位置。  這也可能造成存取違規。  
  
 如果傳入的引數大小大於緩衝區的實際大小， [緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795) 會發生。  
  
## 範例  
 這個程式以長整數 `aclock` 存放系統時間，使用 `asctime_s` 函式，將它轉譯成結構 `newtime` 然後轉換成輸出的字串形式。  
  
```  
// crt_asctime_s.c  
#include <time.h>  
#include <stdio.h>  
  
struct tm newtime;  
__time32_t aclock;  
  
int main( void )  
{  
   char buffer[32];  
   errno_t errNum;  
   _time32( &aclock );   // Get time in seconds.  
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.  
  
   // Print local time as a string.  
  
   errNum = asctime_s(buffer, 32, &newtime);  
   if (errNum)  
   {  
       printf("Error code: %d", (int)errNum);  
       return 1;  
   }  
   printf( "Current date and time: %s", buffer );  
   return 0;  
}  
```  
  
  **Current date and time: Wed May 14 15:30:17 2003**   
## .NET Framework 對等用法  
  
-   <xref:System.DateTime.ToLongDateString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToLongTimeString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToShortDateString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToShortTimeString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToString%2A?displayProperty=fullName>  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)