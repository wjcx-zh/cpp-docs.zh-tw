---
title: localtime_s、_localtime32_s、_localtime64_s
ms.date: 4/2/2020
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
- _o__localtime32_s
- _o__localtime64_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3c5d194da85eb5d008dfc9cf19f222ebb575747d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342127"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s、_localtime32_s、_localtime64_s

將**time_t**時間值轉換為**tm**結構,並更正本地時區。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強的 [localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md) 版本。

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

*來源時間*<br/>
預存時間的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*tmDest*|*來源時間*|傳回值|以*tmD 最大值*|叫用無效的參數處理常式|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**空**|任意|**埃因瓦爾**|未修改|是|
|**非 NULL(** 指向有效記憶體 )|**空**|**埃因瓦爾**|所有的欄位設定為 -1|是|
|**非 NULL(** 指向有效記憶體 )|小於 0 或大於 **_MAX__TIME64_T**|**埃因瓦爾**|所有的欄位設定為 -1|否|

在前兩個錯誤條件的情況下，叫用了無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

**localtime_s**函數轉換存儲為[time_t](../../c-runtime-library/standard-types.md)值的時間,並將結果存儲在[tm](../../c-runtime-library/standard-types.md)類型的結構中。 **time_t**值*源時間*表示自 1970 年 1 月 1 日(UTC)午夜 (00:00:00)起經過的秒數。 此值通常從[時間](time-time32-time64.md)函數獲得。

**localtime_s**如果使用者首先設置全域環境變數**TZ,localtime_s**糾正本地時區。 設置**TZ**時,還會自動設置另外三個環境變數 **(_timezone、_daylight**和 **_tzname)。** **_daylight** 如果未設置**TZ**變數 **,localtime_s**嘗試使用控制面板中的日期/時間應用程式中指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](tzset.md) 中有關於些變數的描述。 **TZ**是微軟的擴展,不是**本地時間的**ANSI 標準定義的一部分。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。

**_localtime64_s**()使用 **__time64_t**結構,允許日期在 3001 年 1 月 18 日 23:59:59(協調通用時間 (UTC) 之前表示,而 **_localtime32_s**表示日期為 2038 年 1 月 18 日 23:59:59,UTC。

**localtime_s**是一個內聯函數,它計算到 **_localtime64_s,time_t**等效於 **__time64_t。** **time_t** 如果需要強制編譯器將**time_t**解釋為舊的 32 位**time_t**,則可以定義 **_USE_32BIT_TIME_T**。 這樣做將導致**localtime_s**評估 **_localtime32_s。** 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

結構類型[tm](../../c-runtime-library/standard-types.md)的欄位儲存以下值,每個值都是**int**。

|欄位|描述|
|-|-|
|**tm_sec**|一分鐘后秒 (0 - 59)。|
|**tm_min**|一小時后幾分鐘 (0 - 59)。|
|**tm_hour**|午夜起(0 - 23日)的上班時間。|
|**tm_mday**|月日(1 - 31)。|
|**tm_mon**|月 (0 - 11;1 月 = 0)。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|星期一(0 - 6;周日 = 0)。|
|**tm_yday**|一年中的日子(0 - 365;1 月 1 = 0)。|
|**tm_isdst**|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。|

如果設置了**TZ**環境變數,C 運行時庫將假定適合美國的規則來實現夏令時 (DST) 的計算。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<ctime\<> 或時間.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
