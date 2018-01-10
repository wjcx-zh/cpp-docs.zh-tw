---
title: "localtime_s、_localtime32_s、_localtime64_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs: C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ddce7d73919e7e7942d8ddd7954ce6cbec4789fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s、_localtime32_s、_localtime64_s
轉換時間值，並依本地時區進行校正。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強的 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### <a name="parameters"></a>參數  
 `_tm`  
 要填入之時間結構的指標。  
  
 `time`  
 預存時間的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`_tm`|`time`|傳回值|`_tm` 中的值|叫用無效的參數處理常式|  
|-----------|------------|------------------|--------------------|---------------------------------------|  
|`NULL`|any|`EINVAL`|未修改|[是]|  
|非 `NULL` (指向有效的記憶體)|`NULL`|`EINVAL`|所有的欄位設定為 -1|[是]|  
|非 `NULL` (指向有效的記憶體)|小於 0 或大於 `_MAX__TIME64_T`|`EINVAL`|所有的欄位設定為 -1|否|  
  
 在前兩個錯誤條件的情況下，叫用了無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_localtime32_s` 函式轉換儲存為 [time_t](../../c-runtime-library/standard-types.md) 值的時間，並將結果儲存在`tm` 類型的結構中。 `long` 值 `timer` 代表從 1970 年 1 月 1 日 UTC 午夜 (00: 00:00) 以來經過的秒數。 這個值通常取自 `time` 函式。  
  
 如果使用者第一次設定全域環境變數 `TZ`，`_localtime32_s` 會為本地時區進行校正。 當已設定 `TZ` 時，其他三個環境變數 (`_timezone`、`_daylight`和 `_tzname`) 也會自動設定。 如果未設定 `TZ` 變數，`localtime32_s` 會嘗試使用控制台中的日期/時間應用程式中指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](../../c-runtime-library/reference/tzset.md) 中有關於些變數的描述。 `TZ` 是 Microsoft 延伸模組，且並不屬於 ANSI 標準定義的 `localtime`。  
  
> [!NOTE]
>  目標環境應該嘗試判斷日光節約時間是否生效。  
  
 `_localtime64_s` 會使用`__time64_t` 結構，允許表示至國際標準時間 (UTC) 3001 年 1 月 18 日 23:59:59 為止的日期，而 `_localtime32_s` 則表示至 2038 年 1 月 18 日 23:59:59 UTC 為止的日期。  
  
 `localtime_s` 是內嵌函式，其評估 `_localtime64_s` 和 `time_t` 是否相當於 `__time64_t`。 如果您要強制編譯器將 `time_t` 解譯為舊的 32 位元 `time_t`，您可以定義 `_USE_32BIT_TIME_T`。 如此一來，將導致 `localtime_s` 評估 `_localtime32_s`。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。  
  
 結構類型 [tm](../../c-runtime-library/standard-types.md) 的欄位儲存下列值，每個值都是 `int`。  
  
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
 若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 如果 `TZ` 環境變數已設定，C 執行階段程式庫將假設適用於美國之規則，以實作日光節約時間 (DST) 的計算。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`localtime_s`|\<time.h>|  
|`_localtime32_s`|\<time.h>|  
|`_localtime64_s`|\<time.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## <a name="see-also"></a>請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)
