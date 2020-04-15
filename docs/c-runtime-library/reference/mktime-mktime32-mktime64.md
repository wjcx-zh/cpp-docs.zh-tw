---
title: mktime、_mktime32、_mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: b0981f33d70945083eacd28eb7517e80b3f2539f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338708"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime、_mktime32、_mktime64

將當地時間轉換成月曆值。

## <a name="syntax"></a>語法

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>參數

*timeptr*<br/>
時間結構的指標，請參閱 [asctime](asctime-wasctime.md)。

## <a name="return-value"></a>傳回值

**_mktime32**返回編碼為[類型time_t](../../c-runtime-library/standard-types.md)的值的指定日曆時間。 如果*timeptr*引用 1970 年 1 月 1 日午夜之前的日期,或者如果無法表示日曆時間 **,_mktime32**傳回 -1 強制轉換以鍵入**time_t**。 使用 **_mktime32**時,如果*timeptr*引用 2038 年 1 月 18 日 23:59:59 之後的日期,則協調通用時間 (UTC)後,它將返回 -1 強制轉換以鍵入**time_t**。

如果*時間點*引用日期 23:59:59,3000 年 12 月 31 日之後的日期 **,_mktime64**將返回 -1 強制轉換以鍵入 **__time64_t。**

## <a name="remarks"></a>備註

**mktime、_mktime32**和 **_mktime64**函數將*timeptr*指向的提供的時間結構(可能不完整)轉換為具有規範化值的完全定義的結構,然後將其轉換為 **_mktime32****time_t**日曆時間值。 轉換後的時間和 [time](time-time32-time64.md) 函式傳回的值具有相同的編碼。 忽略*時計*結構**tm_wday**和**tm_yday**元件的原始值,其他元件的原始值不限於其正常範圍。

**mktime**是等效於 **_mktime64**的內聯函數,除非定義了 **_USE_32BIT_TIME_T,** 在這種情況下,它等效於 **_mktime32**。

調整到 UTC 後 **,_mktime32**處理從 1970 年 1 月 1 日午夜到 2038 年 1 月 18 日 23:59:59 UTC 的日期。 **_mktime64**處理日期從 1970 年 1 月 1 日午夜到 23:59:59,12 月 31 日,3000 年 12 月 31 日。 此調整可能導致這些函數返回 -1(強制轉換為**time_t、__time32_t**或 **__time64_t),** 即使您指定 **__time32_t**的日期在範圍內。 例如，您在開羅 (埃及)，此地區比 UTC 快兩小時，因此會先將 *timeptr* 中您指定的日期減去兩小時；而這麼做可能會使您的日期落在範圍之外。

可能會使用這些函式進行驗證及填寫 tm 結構。 如果成功,這些函數將**tm_wday**和**tm_yday**的值設置為適當的,並將其他元件設置為表示指定的日曆時間,但其值強制為正常範圍。 在確定**tm_mon**和**tm_year**之前,不會設置**tm_mday**的最終值。 指定**tm**結構時間時,將**tm_isdst**欄位設定為:

- 零 (0)，以指出標準時間已生效。

- 大於 0 的值，以指出日光節約時間已生效。

- 小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。

C 執行階段程式庫會從 [TZ](tzset.md) 環境變數判斷日光節約時間行為。 如果未**TZ**設置 TZ,Win32 API 調用[GetTimeZone 資訊](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation)用於從作業系統獲取夏令時資訊。 若此作業失敗，程式庫會在實作日光節約時間的計算時，假定使用美國的規則。 **tm_isdst**是必填欄位。 若無設定，該值會是未定義，而且這些函式的傳回值會無法預期。 如果*timeptr*指向以前呼叫[asctime、gmtime](asctime-wasctime.md)或[本地時間](localtime-localtime32-localtime64.md)(或這些函數的變數)傳回的**tm**結構,則[gmtime](gmtime-gmtime32-gmtime64.md)**tm_isdst**欄位包含正確的值。

請注意 **,gmtime**和**本地時間**(以及 **_gmtime32**_gmtime32、_gmtime64、_localtime32 **_gmtime64**和 **_localtime64)** 使用每個線程的單 **_localtime32**個緩衝區進行轉換。 如果向**mktime、_mktime32**或 **_mktime32** **_mktime64**提供此緩衝區,則以前的內容將被銷毀。

這些函式會驗證它們的參數。 如果 *timeptr* 為 null 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回 -1 並將**errno**設定為**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>範例輸出

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
