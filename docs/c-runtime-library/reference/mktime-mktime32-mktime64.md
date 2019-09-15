---
title: mktime、_mktime32、_mktime64
ms.date: 11/04/2016
api_name:
- _mktime32
- mktime
- _mktime64
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
ms.openlocfilehash: a282e9f27a0e8f2a91219facda96a5929d3982ea
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951526"
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

**_mktime32**會傳回指定的行事歷時間，並編碼為[time_t](../../c-runtime-library/standard-types.md)類型的值。 如果*timeptr*參考1970年1月1日午夜之前的日期，或如果無法表示行事歷時間， **_mktime32**會傳回-1 轉換成類型**time_t**。 使用 **_mktime32**時，如果*timeptr*參考的23:59:59 日期是2038年1月18日（國際標準時間（UTC）），則會傳回-1 轉換成類型**time_t**。

如果*timeptr*參考23:59:59 年12月 3000 31 日（UTC）之後的日期， **_mktime64**會傳回-1 轉換成類型 **__time64_t** 。

## <a name="remarks"></a>備註

**Mktime**、 **_mktime32**和 **_mktime64**函式會將*timeptr*指向的提供時間結構（可能不完整）轉換成具有正規化值的完整定義結構，然後將它轉換成**time_t**行事曆時間值。 轉換後的時間和 [time](time-time32-time64.md) 函式傳回的值具有相同的編碼。 系統會忽略*timeptr*結構之**tm_wday**和**tm_yday**元件的原始值，而其他元件的原始值則不會限制為其一般範圍。

**mktime**是相當於 **_mktime64**的內嵌函式，除非已定義 **_USE_32BIT_TIME_T** ，在此情況下，它相當於 **_mktime32**。

調整到 UTC 之後， **_mktime32**會處理從1970年1月1日午夜到23:59:59 年1月 18 2038 日（utc）的日期。 **_mktime64**會處理從1970年1月1日午夜到23:59:59，3000年12月31日午夜的日期。 這項調整可能會導致這些函式傳回-1 （轉換成**time_t**、 **__time32_t**或 **__time64_t**），即使您指定的日期是在範圍內也一樣。 例如，您在開羅 (埃及)，此地區比 UTC 快兩小時，因此會先將 *timeptr* 中您指定的日期減去兩小時；而這麼做可能會使您的日期落在範圍之外。

可能會使用這些函式進行驗證及填寫 tm 結構。 如果成功，這些函式會適當地設定**tm_wday**和**tm_yday**的值，並將其他元件設定為代表指定的行事歷時間，但其值會強制至正常範圍。 在決定**tm_mon**和**tm_year**之前，不會設定**tm_mday**的最終值。 指定**tm**結構時間時，請將**tm_isdst**欄位設定為：

- 零 (0)，以指出標準時間已生效。

- 大於 0 的值，以指出日光節約時間已生效。

- 小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。

C 執行階段程式庫會從 [TZ](tzset.md) 環境變數判斷日光節約時間行為。 如果未設定**TZ** ，則會使用 WIN32 API 呼叫[GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation)來取得作業系統的日光節約時間資訊。 若此作業失敗，程式庫會在實作日光節約時間的計算時，假定使用美國的規則。 **tm_isdst**是必要欄位。 若無設定，該值會是未定義，而且這些函式的傳回值會無法預期。 如果*timeptr*指向先前呼叫[asctime](asctime-wasctime.md)、 [gmtime](gmtime-gmtime32-gmtime64.md)或[localtime](localtime-localtime32-localtime64.md)所傳回的**tm**結構（或這些函式的變體）， **tm_isdst**欄位會包含正確的值。

請注意， **gmtime**和**localtime** （**以及 _gmtime32**、 **_gmtime64**、 **_localtime32**和 **_localtime64**）在每個執行緒中都使用單一緩衝區來進行轉換。 如果您將此緩衝區提供給**mktime**、 **_mktime32**或 **_mktime64**，則會終結先前的內容。

這些函式會驗證它們的參數。 如果 *timeptr* 為 null 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回-1，並將**errno**設為**EINVAL**。

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
