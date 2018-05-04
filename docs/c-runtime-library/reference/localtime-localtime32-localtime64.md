---
title: localtime、_localtime32、_localtime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 778b2d214551c5848dd091e33dbbab1814544fb4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="localtime-localtime32-localtime64"></a>localtime，_localtime32，_localtime64

轉換時間值，並依本地時區進行校正。 這些函式有更安全的版本可供使用；請參閱 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)。

## <a name="syntax"></a>語法

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>參數

*sourceTime*<br/>
預存時間的指標。

## <a name="return-value"></a>傳回值

結構的結果，傳回的指標或**NULL**日期傳遞至函式是否：

- 1970 年 1 月 1 日午夜之前。

- 在 03:14:07，2038 年 1 月 19 日，UTC 之後 (使用 **_time32**和**time32_t**)。

- 23:59:59，3000 年 12 月 31 日 UTC 之後 (使用 **_time64**和 **__time64_t**)。

**_localtime64**，它會使用 **__time64_t**結構時，請允許向上 23:59:59，3000 年 12 月 31 日，國際標準時間 (UTC) 表示的日期，而 **_localtime32**代表 23:59:59 2038 年 1 月 18 日，UTC 日期。

**localtime**是內嵌函式，而它評估成 **_localtime64**，和**time_t**相當於 **__time64_t**。 如果您要強制編譯器將解譯**time_t**為舊的 32 位元**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 如此一來，這會導致**localtime**評估為 **_localtime32**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

結構類型的欄位[tm](../../c-runtime-library/standard-types.md)儲存下列的值，其中每個**int**:

|欄位|描述|
|-|-|
|**tm_sec**|分鐘之後的秒數 (0-59)。|
|**tm_min**|小時之後的分鐘 (0-59)。|
|**tm_hour**|從午夜開始的小時 (0-23)。|
|**tm_mday**|日期的月份 (1-31)。|
|**tm_mon**|月 (0-11。年 1 月 = 0）。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|一週天數 (0-6;星期日 = 0）。|
|**tm_yday**|年中的日 (0-365;年 1 月 1 = 0)。|
|**tm_isdst**|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。|

如果**TZ**設定環境變數時，C 執行階段程式庫假設規則適用於美國實作日光節約時間 (DST) 的計算。

## <a name="remarks"></a>備註

**Localtime**函式將儲存為時間轉換[time_t](../../c-runtime-library/standard-types.md)值，並將結果儲存類型的結構[tm](../../c-runtime-library/standard-types.md)。 **長**值*sourceTime*代表從午夜以來經過的秒數 (00: 00:00)、 1970 年 1 月 1 日 UTC。 這個值通常取自[時間](time-time32-time64.md)函式。

這兩個 32 位元和 64 位元版本的[gmtime](gmtime-gmtime32-gmtime64.md)， [mktime](mktime-mktime32-mktime64.md)， [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)，和**localtime**全都使用單一**tm**每個執行緒來進行轉換的結構。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

**localtime**更正當地時區，如果使用者第一次設定全域環境變數**TZ**。 當**TZ**設定，其他三個環境變數 (**_timezone**， **_daylight**，和 **_tzname**) 也會自動設定。 如果**TZ**未設定變數， **localtime**嘗試使用 [控制台] 中的日期/時間應用程式指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](tzset.md) 中有關於些變數的描述。 **TZ**是 Microsoft 擴充功能並不屬於 ANSI 標準定義的**localtime**。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。

這些函式會驗證它們的參數。 如果*sourceTime*為 null 指標，或如果*sourceTime*值為負數，這些函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行，函式會傳回**NULL**並設定**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**localtime**， **_localtime32**， **_localtime64**|\<time.h>|\<ctime > 或\<h >|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
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

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
