---
title: "時間管理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "日期，執行階段程式庫成員"
  - "時間，時間管理"
  - "日期函式"
  - "時間函式"
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# 時間管理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用這些函式取得目前的時間，以及在必要時轉換、調整及儲存該時間。 目前的時間為系統時間。  
  
 `_ftime`  及 `localtime` 常式會使用 `TZ` 環境變數。 若未設定 `TZ`，執行階段程式庫會嘗試使用作業系統所指定的時區資訊。 若無法使用這項資訊，這些函式會使用預設值 PST8PDT。 如需 `TZ` 的詳細資訊，請參閱 [\_tzset](../c-runtime-library/reference/tzset.md)；另請參閱 [\_daylight、timezone 及 \_tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)。  
  
### 時間常式  
  
|函式|用法|.NET Framework 同等|  
|--------|--------|-----------------------|  
|[asctime、\_wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime\_s、\_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|將時間從類型 `struct tm` 轉換為字元字串 這些具有 `_s` 尾碼的函式版本比較安全。|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[時鐘](../c-runtime-library/reference/clock.md)|傳回處理序的耗用時鐘時間。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [\_ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|將時間從類型 `time_t`、`__time32_t` 或 `__time64_t` 轉換為字元字串。 這些具有 `_s` 尾碼的函式版本比較安全。|[System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)|  
|[difftime、\_difftime32、\_difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|計算兩個時間之間的差異。|[System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[\_ftime、\_ftime32、\_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)、[\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|將目前的系統時間儲存在類型 `struct _timeb` 或類型 `struct``__timeb64` 的變數中。這些具有 `_s` 尾碼的函式版本比較安全。|[System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)|  
|[\_futime、\_futime32、\_futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|對開啟的檔案上設定修改時間|[System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx), [System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx), [System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)|  
|[gmtime、\_gmtime32、\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|將時間從類型 `time_t` 轉換為 `struct tm`，或從類型 `__time64_t` 轉換為 `struct tm`。這些具有 `_s` 尾碼的函式版本比較安全。|[System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx), [System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)|  
|[localtime，\_localtime32，\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime\_s、\_localtime32\_s、\_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|將時間從類型 `time_t` 轉換為 `struct tm`，或從類型 `__time64_t` 轉換為經過本機校正的 `struct tm`。 這些具有 `_s` 尾碼的函式版本比較安全。|[System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)|  
|[\_mkgmtime、\_mkgmtime32、\_mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|將時間轉換為格林威治標準時間的月曆值。|[System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)|  
|[mktime、\_mktime32、\_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|將時間轉換為月曆值。|[System::DateTime::DateTime](Overload:System.DateTime.)|  
|[\_strdate、\_wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [\_strdate\_s、\_wstrdate\_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|以字串形式傳回目前的系統日期。 這些具有 `_s` 尾碼的函式版本比較安全。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|將日期與時間字串格式化成國際通用的格式。|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[\_strtime、\_wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [\_strtime\_s、\_wstrtime\_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|以字串形式傳回目前的系統時間。 這些具有 `_s` 尾碼的函式版本比較安全。|[System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx), [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx), [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx), [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx), [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)|  
|[time、\_time32、\_time64](../c-runtime-library/reference/time-time32-time64.md)|取得目前的系統時間，類型為 `time_t`、 `__time32_t` 或 `__time64_t`。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_tzset](../c-runtime-library/reference/tzset.md)|從環境時間變數 `TZ` 設定外部時間變數 。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_utime、\_utime32、\_utime64、\_wutime、\_wutime32、\_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|使用目前的時間或結構中儲存的時間值，為指定的檔案設定修改時間。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
> [!NOTE]
>  在所有的 Microsoft C\/C\+\+ 版本 \(Microsoft C\/C\+\+ 7.0 版除外\) 及所有的 Visual C\+\+ 版本中，時間函式會傳回自 1970 年 1 月 1 日午夜起算所經過的秒數作為目前的時間。 在 Microsoft C\/C\+\+ 7.0 版中，`time`  會傳回自 1899 年 12 月 31 日午夜起算所經過的秒數作為目前的時間。  
  
> [!NOTE]
>  在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 版本及 Visual C\+\+ 2005 之前的 Microsoft C\/C\+\+ 版本中，因為 `time_t`  是 `long int`  \(32 位元\)，所以自 2038 年 1 月 19 日 3:14:07 UTC 之後便無法使用。 現在 `time_t`  預設等同於 `__time64_t`，但定義 `_USE_32BIT_TIME_T`  會將 `time_t`  變更為 `__time32_t` ，並強制許多時間函式呼叫需要取用 32 位元 `time_t` 的版本。 如需詳細資訊，請參閱[標準類型](../c-runtime-library/standard-types.md)與個別時間函式文件中的註解。  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)