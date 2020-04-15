---
title: localtime，_localtime32，_localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
ms.openlocfilehash: 21496b71c354c7bed7b87526dc40bc9b24865da2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342129"
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

*來源時間*<br/>
預存時間的指標。

## <a name="return-value"></a>傳回值

傳回指向結構結果的指標 **,如果傳遞給**函數的日期為:

- 1970 年 1 月 1 日午夜之前。

- 在 2038 年 1 月 19 日 03:14:07 之後,UTC(使用 **_time32**和**time32_t)。**

- 在 23:59:59, 12 月 31, 3000, UTC (使用 **_time64**和 **__time64_t**) 之後。

**_localtime64**(_localtime64 使用 **__time64_t**結構,允許日期在 2000 年 12 月 31 日 23:59:59(協調通用時間 (UTC) 之前表示,而 **_localtime32**表示日期為 2038 年 1 月 18 日 23:59:59,UTC。

**當地時間**是一個內聯函數,它計算為 **_localtime64,time_t**相當於**time_t****__time64_t。** 如果需要強制編譯器將**time_t**解釋為舊的 32 位**time_t**,則可以定義 **_USE_32BIT_TIME_T**。 這樣做將導致**當地時間**評估到 **_localtime32**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

結構類型[tm](../../c-runtime-library/standard-types.md)的欄位儲存以下值,每個值都是**int**:

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

## <a name="remarks"></a>備註

**本地時間**函數轉換存儲為[time_t](../../c-runtime-library/standard-types.md)值的時間,並將結果存儲在[tm](../../c-runtime-library/standard-types.md)類型的結構中。 **長**值*源時間*表示自午夜 (00:00:00) 到 UTC 1970 年 1 月 1 日以來的秒數。 此值通常從[時間](time-time32-time64.md)函數獲得。

**tm** gmtime、mktime、mkgmtime 和**本地時間的**32[mktime](mktime-mktime32-mktime64.md)位元和[mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)64 位元版本都使用每個執行緒[gmtime](gmtime-gmtime32-gmtime64.md)的單個 tm 結構進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。

如果使用者首先設置全域環境變數**TZ,** 則本地時區的**本地時間**更正。 設置**TZ**時,還會自動設置另外三個環境變數 **(_timezone、_daylight**和 **_tzname)。** **_daylight** 如果未設定**TZ**變數,**則本地時間**嘗試使用控制面板中的日期/ 時間應用程式中指定的時區資訊。 如果無法取得這些資訊，則預設使用代表太平洋時區的 PST8PDT。 請參閱 [_tzset](tzset.md) 中有關於些變數的描述。 **TZ**是微軟的擴展,不是**本地時間的**ANSI 標準定義的一部分。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。

這些函式會驗證它們的參數。 如果*sourceTime*是空指標,或者如果*sourceTime*值為負,則這些函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回**NULL**並將**errno**設定為**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**當地時間****_localtime32_localtime64** **_localtime64**|\<time.h>|\<ctime\<> 或時間.h>|

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
