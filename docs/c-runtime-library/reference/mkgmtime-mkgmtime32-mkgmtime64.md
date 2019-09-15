---
title: _mkgmtime、_mkgmtime32、_mkgmtime64
ms.date: 11/04/2016
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
ms.openlocfilehash: fcd1e3fdcca37d7e5bb381c234a6d8555ce2766c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951674"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64

將**結構** **tm**所代表的 utc 時間，轉換為**TIME_T**類型所代表的 utc 時間。

## <a name="syntax"></a>語法

```C
time_t _mkgmtime(
   struct tm* timeptr
);
__time32_t _mkgmtime32(
   struct tm* timeptr
);
__time64_t _mkgmtime64(
   struct tm* timeptr
);
```

### <a name="parameters"></a>參數

*timeptr*<br/>
要轉換之**結構** **tm**的 UTC 時間指標。

## <a name="return-value"></a>傳回值

**__Time32_t**或 **__time64_t**類型的數量，代表自1970年1月1日午夜（以國際標準時間（UTC）為單位）所經過的秒數。 如果日期超出範圍（請參閱「備註」一節），或無法將輸入解讀為有效的時間，則傳回值為-1。

## <a name="remarks"></a>備註

**_Mkgmtime32**和 **_mkgmtime64**函式會將 utc 時間轉換成代表 utc 時間的 **__time32_t**或 **__time64_t**類型。 若要將當地時間轉換成 UTC 時間，請改用**mktime**、 **_mktime32**和 **_mktime64** 。

**_mkgmtime**是評估為 **_mkgmtime64**的內嵌函式，而**time_t**相當於 **__time64_t**。 如果您需要強制編譯器將**time_t**解讀為舊版32位**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 不建議您這樣做，因為您的應用程式可能會在2038年1月18日之後失敗（32位**time_t**的最大範圍），而且不允許在64位平臺上使用。

傳入的時間結構會如下所示變更，其方式與使用 **_mktime**函數變更時相同： **tm_wday**和**tm_yday**欄位會根據**tm_mday**和**tm_year**的值設定為新的值。 指定**tm**結構時間時，請將**tm_isdst**欄位設定為：

- 零 (0)，以指出標準時間已生效。

- 大於 0 的值，以指出日光節約時間已生效。

- 小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。

C 執行階段程式庫使用 TZ 環境變數來判斷正確的日光節約時間。 如果未設定 TZ，則會查詢作業系統以取得正確的地區日光節約時間行為。 **tm_isdst**是必要欄位。 如果未設定，則其值為未定義，且來自**mktime**的傳回值無法預測。

**_Mkgmtime32**函數的範圍是從1970年1月1日午夜，utc 到23:59:59 年1月 18 2038 日，utc。 **_Mkgmtime64**的範圍是從1970年1月1日午夜，utc 到23:59:59 年12月 31 3000 日（utc）。 超出範圍的日期會產生-1 的傳回值。 **_Mkgmtime**的範圍取決於是否已定義 **_USE_32BIT_TIME_T** 。 如果未定義（預設值），則範圍是 **_mkgmtime64**的。否則，範圍會限制為32位的 **_mkgmtime32**範圍。

請注意， **gmtime**和**localtime**會使用單一靜態配置的緩衝區來進行轉換。 如果您將此緩衝區提供給**mkgmtime**，則會終結先前的內容。

## <a name="example"></a>範例

```C
// crt_mkgmtime.c
#include <stdio.h>
#include <time.h>

int main()
{
    struct tm t1, t2;
    time_t now, mytime, gmtime;
    char buff[30];

    time( & now );

    _localtime64_s( &t1, &now );
    _gmtime64_s( &t2, &now );

    mytime = mktime(&t1);
    gmtime = _mkgmtime(&t2);

    printf("Seconds since midnight, January 1, 1970\n");
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);

    /* Use asctime_s to display these times. */

    _localtime64_s( &t1, &mytime );
    asctime_s( buff, sizeof(buff), &t1 );
    printf( "Local Time: %s\n", buff );

    _gmtime64_s( &t2, &gmtime );
    asctime_s( buff, sizeof(buff), &t2 );
    printf( "Greenwich Mean Time: %s\n", buff );

}
```

### <a name="sample-output"></a>範例輸出

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

下列範例示範如何以星期幾和年份日期的計算值填滿不完整的結構。

```C
// crt_mkgmtime2.c
#include <stdio.h>
#include <time.h>
#include <memory.h>

int main()
{
    struct tm t1, t2;
    time_t gmtime;
    char buff[30];

    memset(&t1, 0, sizeof(struct tm));
    memset(&t2, 0, sizeof(struct tm));

    t1.tm_mon = 1;
    t1.tm_isdst = 0;
    t1.tm_year = 103;
    t1.tm_mday = 12;

    // The day of the week and year will be incorrect in the output here.
    asctime_s( buff, sizeof(buff), &t1);
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

    gmtime = _mkgmtime(&t1);

    // The correct day of the week and year were determined.
    asctime_s( buff, sizeof(buff), &t1);
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",
            buff, t1.tm_yday );

}
```

### <a name="output"></a>Output

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
