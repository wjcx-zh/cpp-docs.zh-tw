---
title: "localtime、_localtime32、_localtime64 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _localtime64
- _localtime32
- localtime
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
dev_langs:
- C++
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 6dcb9a6f0d7187722a769a28cfb624e4621c181f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="localtime-localtime32-localtime64"></a>localtime，_localtime32，_localtime64
轉換時間值，並依本地時區進行校正。 這些函式有更安全的版本可供使用；請參閱 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
struct tm *localtime(  
   const time_t *timer   
);  
struct tm *_localtime32(  
   const __time32_t *timer  
);  
struct tm *_localtime64(  
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>參數  
 `timer`  
 預存時間的指標。  
  
## <a name="return-value"></a>傳回值  
 將指標傳回結構結果，或 `NULL`，如果傳遞給函式的日期是︰  
  
-   1970 年 1 月 1 日午夜之前。  
  
-   2038 年 1 月 19 日 03:14:07 UTC 之後 (使用`_time32` 和 `time32_t`)。  
  
-   3000 年 12 月 31 日 23:59:59 UTC 之後 (使用`_time64` 和 `__time64_t`)。  
  
 使用 `__time64_t` 結構的`_localtime64`，允許表示至國際標準時間 (UTC) 3000 年 12 月 31 日 23:59:59 為止的日期，而 `_localtime32` 則表示至 2038 年 1 月 18 日23:59:59 UTC為止的日期。  
  
 `localtime` 是內嵌函式，其評估 `_localtime64` 和`time_t` 是否相當於`__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元`time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，將導致 `localtime` 評估 `_localtime32`。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。  
  
 結構類型 [tm](../../c-runtime-library/standard-types.md) 的欄位儲存下列值，每個值都是 `int`：  
  
 `tm_sec`  
 分鐘之後的秒數 (0-59)。  
  
 `tm_min`  
 小時之後的分鐘 (0-59)。  
  
 `tm_hour`  
 午夜之後的小時 (0-23)。  
  
 `tm_mday`  
 日期的月份 (1-31)。  
  
 `tm_mon`  
 月 (0-11。年 1 月 = 0）。  
  
 `tm_year`  
 年份 (目前年份減去 1900)。  
  
 `tm_wday`  
 一週天數 (0-6;星期日 = 0）。  
  
 `tm_yday`  
 年中的日 (0-365;年 1 月 1 = 0)。  
  
 `tm_isdst`  
 若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 如果已設定 `TZ` 環境變數，C 執行階段程式庫將假設適用於美國之規則，以實作日光節約時間 (DST) 的計算。  
  
## <a name="remarks"></a>備註  
 `localtime` 函式轉換儲存為 [time_t](../../c-runtime-library/standard-types.md) 值的時間，並將結果儲存在`tm` 類型的結構中。 `long` 值 `timer` 代表從 1970 年 1 月 1 日 UTC 午夜 (00: 00:00) 以來經過的秒數。 這個值通常取自 `time` 函式。  
  
 32 位元和 64 位元版本的 `gmtime`、`mktime`、`mkgmtime`，和 `localtime` 進行轉換時每個執行緒都使用單一的 `tm` 結構。 每呼叫其中一個此類常式會導致先前呼叫結果的終結。  
  
 如果使用者第一次設定全域環境變數 `TZ`，`localtime` 會為本地時區進行校正。 當已設定 `TZ` 時，其他三個環境變數 (`_timezone`、`_daylight`和 `_tzname`) 也會自動設定。 如果未設定 `TZ` 變數，`localtime` 會嘗試使用控制台中的日期/時間應用程式中指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 中有關於些變數的描述。 `TZ` 是 Microsoft 延伸模組，且並不屬於 ANSI 標準定義的 `localtime`。  
  
> [!NOTE]
>  目標環境應該嘗試判斷日光節約時間是否生效。  
  
 這些函式會驗證它們的參數。 如果 `timer` 是 Null 指標，或如果計時器值為負值，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回 `NULL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`localtime`|\<time.h>|  
|`_localtime32`|\<time.h>|  
|`_localtime64`|\<time.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_localtime.cpp  
// compile with: /W3  
/* This program uses _time64 to get the current time   
 * and then uses localtime64() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm *newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
  
        _time64( &long_time );           // Get time as 64-bit integer.  
                                         // Convert to local time.  
        newtime = _localtime64( &long_time ); // C4996  
        // Note: _localtime64 deprecated; consider _localetime64_s  
  
        if( newtime->tm_hour > 12 )        // Set up extension.  
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime->tm_hour > 12 )        // Convert from 24-hour  
                newtime->tm_hour -= 12;    //   to 12-hour clock.  
        if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime->tm_hour = 12;  
  
        char buff[30];  
        asctime_s( buff, sizeof(buff), newtime );  
        printf( "%.19s %s\n", buff, am_pm );  
}  
```  
  
```Output  
Tue Feb 12 10:05:58 AM  
```  
  
## <a name="see-also"></a>另請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)
