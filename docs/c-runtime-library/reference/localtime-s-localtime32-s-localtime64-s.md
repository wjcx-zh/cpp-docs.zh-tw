---
title: localtime_s、_localtime32_s、_localtime64_s
ms.date: 07/09/2019
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: c00a5d23441612d0e70bfafd571bcb25250edb09
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953331"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s、_localtime32_s、_localtime64_s

將**time_t**時間值轉換成**tm**結構，並針對當地時區進行更正。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強的 [localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>參數

*tmDest*<br/>
要填入之時間結構的指標。

*sourceTime*<br/>
預存時間的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*tmDest*|*sourceTime*|傳回值|*TmDest*中的值|叫用無效的參數處理常式|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|any|**EINVAL**|未修改|是|
|Not **Null** （指向有效的記憶體）|**NULL**|**EINVAL**|所有的欄位設定為 -1|是|
|Not **Null** （指向有效的記憶體）|小於0或大於 **_MAX__TIME64_T**|**EINVAL**|所有的欄位設定為 -1|否|

在前兩個錯誤狀況的情況下，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會將**errno**設定為**EINVAL** , 並傳回**EINVAL**。

## <a name="remarks"></a>備註

**Localtime_s**函式會將儲存的時間轉換為[time_t](../../c-runtime-library/standard-types.md)值，並將結果儲存在類型為[tm](../../c-runtime-library/standard-types.md)的結構中。 **Time_t**值*sourceTime*代表自1970年1月1日午夜（00:00:00）起算的秒數（UTC）。 這個值通常是從[time](time-time32-time64.md)函數取得。

如果使用者第一次設定全域環境變數**TZ**，則**localtime_s**會更正當地時區。 若設定了**TZ** ，則也會自動設定其他三個環境變數（ **_timezone**、 **_daylight**和 **_tzname**）。 如果未設定**TZ**變數， **localtime_s**會嘗試使用 [控制台] 中的 [日期/時間] 應用程式所指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](tzset.md) 中有關於些變數的描述。 **TZ**是 Microsoft 擴充功能，不屬於**localtime**的 ANSI 標準定義。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。

使用 **__time64_t**結構的 **_localtime64_s**可讓日期以23:59:59 年1月18日3001，國際標準時間（UTC）表示，而 **_Localtime32_s**代表日期到23:59:59 年1月18日2038，UTC。

**localtime_s**是評估為 **_localtime64_s**的內嵌函式，而**time_t**相當於 **__time64_t**。 如果您需要強制編譯器將**time_t**解讀為舊版32位**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 這麼做會導致**localtime_s**評估為 **_localtime32_s**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

結構類型[tm](../../c-runtime-library/standard-types.md)的欄位會儲存下列值，其中每一個都是**int**。

|欄位|描述|
|-|-|
|**tm_sec**|分鐘後的秒數（0-59）。|
|**tm_min**|小時之後的分鐘（0-59）。|
|**tm_hour**|午夜後的小時（0-23）。|
|**tm_mday**|月中的日（1-31）。|
|**tm_mon**|月份（0-11;1月 = 0）。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|周中的日（0-6;星期日 = 0）。|
|**tm_yday**|年中的日（0-365;1月1日 = 0）。|
|**tm_isdst**|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。|

如果已設定**TZ**環境變數，則 C 執行時間程式庫會假設適用于美國的規則，以執行日光節約時間（DST）的計算。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**localtime_s**、 **_localtime32_s**、 **_localtime64_s**|\<time.h>|\<ctime > 或\<time. h >|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

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
        newtime.tm_hour -= 12;        // to 12-hour clock.
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

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
