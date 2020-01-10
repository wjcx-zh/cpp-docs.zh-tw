---
title: localtime，_localtime32，_localtime64
ms.date: 11/04/2016
api_name:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 7e2f39b3a1b6376e24d8a812d1074840862f398a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953351"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime，_localtime32，_localtime64

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

傳回結構結果的指標，如果傳遞至函數的日期為，則為**Null** ：

- 1970 年 1 月 1 日午夜之前。

- 03:14:07 年1月 2038 19 日之後，UTC （使用 **_time32**和**time32_t**）。

- 23:59:59 年12月 3000 31 日，UTC （使用 **_time64**和 **__time64_t**）。

使用 **__time64_t**結構的 **_localtime64**可讓日期以23:59:59 年12月31日3000，國際標準時間（UTC）表示，而 **_localtime32**則代表日期到23:59:59 年1月18日，2038，UTC.

**localtime**是評估為 **_localtime64**的內嵌函式，而**time_t**相當於 **__time64_t**。 如果您需要強制編譯器將**time_t**解讀為舊版32位**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 這麼做會導致**localtime**評估為 **_localtime32**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

結構類型[tm](../../c-runtime-library/standard-types.md)的欄位會儲存下列值，其中每一個都是**int**：

|欄位|說明|
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

## <a name="remarks"></a>備註

**Localtime**函式會將儲存的時間轉換為[time_t](../../c-runtime-library/standard-types.md)值，並將結果儲存在類型為[tm](../../c-runtime-library/standard-types.md)的結構中。 **Long**值*sourceTime*代表自1970年1月1日午夜（00:00:00）起算的秒數（UTC）。 這個值通常是從[time](time-time32-time64.md)函數取得。

32位和64位版本的[gmtime](gmtime-gmtime32-gmtime64.md)、 [mktime](mktime-mktime32-mktime64.md)、 [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)和**localtime**都使用每個執行緒的單一**tm**結構來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

如果使用者第一次設定全域環境變數**TZ**，則**localtime**會更正當地時區。 若設定了**TZ** ，則也會自動設定其他三個環境變數（ **_timezone**、 **_daylight**和 **_tzname**）。 如果未設定**TZ**變數， **localtime**會嘗試使用 [控制台] 中的 [日期/時間] 應用程式所指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](tzset.md) 中有關於些變數的描述。 **TZ**是 Microsoft 擴充功能，不屬於**localtime**的 ANSI 標準定義。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。

這些函式會驗證它們的參數。 如果*sourceTime*為 null 指標，或如果*sourceTime*值為負數，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**localtime**、 **_localtime32**、 **_localtime64**|\<time.h>|\<ctime > 或\<time. h >|

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
