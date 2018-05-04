---
title: mktime、_mktime32、_mktime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d02ae8e38a0d3e3b56b5ae69ddd937ef99d76b2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mktime-mktime32-mktime64"></a>mktime、_mktime32、_mktime64

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

**_mktime32**傳回編碼類型的值為指定的月曆時間[time_t](../../c-runtime-library/standard-types.md)。 如果*timeptr*參考 1970 年 1 月 1 日的午夜之前的日期或如果無法表示月曆時間， **_mktime32**傳回-1 轉換為類型**time_t**。 當使用 **_mktime32**如果*timeptr*參考的日期之後 23:59:59 2038 年 1 月 18 日，Coordinated Universal Time (UTC)，它會傳回-1 轉換為類型**time_t**。

**_mktime64**會傳回-1 轉換為類型 **__time64_t**如果*timeptr*參考 23:59:59，3000 年 12 月 31 日 UTC 之後的日期。

## <a name="remarks"></a>備註

**Mktime**， **_mktime32**和 **_mktime64**函式提供的時間結構轉換 （可能不完整） 所指向*timeptr*成完整定義與結構標準化值，然後再轉換成**time_t**月曆時間值。 轉換後的時間和 [time](time-time32-time64.md) 函式傳回的值具有相同的編碼。 原始值**tm_wday**和**tm_yday**元件*timeptr*結構都會被忽略，且其他元件的原始值不受限制其正確的範圍。

**mktime**是內嵌函式相當於 **_mktime64**，除非 **_USE_32BIT_TIME_T**定義，在此情況下它相當於 **_mktime32**.

調整為 UTC 之後, **_mktime32**控點的日期從 1970 年 1 月 1 日午夜到 23:59:59 2038 年 1 月 18 日，UTC。 **_mktime64**日期午夜，自 1970 年 1 月 1 日 23:59:59 3000 年 12 月 31 日的控制代碼。 這項調整可能會造成這些函式傳回-1 (轉型為**time_t**， **__time32_t**或 **__time64_t**) 即使您指定的日期範圍內。 例如，您在開羅 (埃及)，此地區比 UTC 快兩小時，因此會先將 *timeptr* 中您指定的日期減去兩小時；而這麼做可能會使您的日期落在範圍之外。

可能會使用這些函式進行驗證及填寫 tm 結構。 如果成功，這些函式設定的值**tm_wday**和**tm_yday**適當，並設定其他元件，以表示指定的月曆時間，但為 normal 強迫這些值範圍。 最終值**tm_mday**之前未設定**tm_mon**和**tm_year**所決定。 當指定**tm**結構時間時，請設定**tm_isdst**欄位設為：

- 零 (0)，以指出標準時間已生效。

- 大於 0 的值，以指出日光節約時間已生效。

- 小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。

C 執行階段程式庫會從 [TZ](tzset.md) 環境變數判斷日光節約時間行為。 如果**TZ**未設定，Win32 API 呼叫[GetTimeZoneInformation](http://msdn.microsoft.com/library/windows/desktop/ms724421.aspx)用來從作業系統取得日光節約時間資訊。 若此作業失敗，程式庫會在實作日光節約時間的計算時，假定使用美國的規則。 **tm_isdst**是必要的欄位。 若無設定，該值會是未定義，而且這些函式的傳回值會無法預期。 如果*timeptr*指向**tm**先前呼叫所傳回的結構[asctime](asctime-wasctime.md)， [gmtime](gmtime-gmtime32-gmtime64.md)，或[localtime](localtime-localtime32-localtime64.md)（或變異數，這些函式）， **tm_isdst**欄位包含正確的值。

請注意， **gmtime**和**localtime** (和 **_gmtime32**， **_gmtime64**， **_localtime32**，和 **_localtime64**) 使用單一緩衝區每個執行緒來進行轉換。 如果您提供此緩衝區**mktime**， **_mktime32**或 **_mktime64**，先前的內容將被終結。

這些函式會驗證它們的參數。 如果 *timeptr* 為 null 指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回-1，並設定**errno**至**EINVAL**。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
