---
title: _mkgmtime、_mkgmtime32、_mkgmtime64
ms.date: 11/04/2016
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
ms.openlocfilehash: 65d96d79a45e05e4b371315c0612ed086f6ea2a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156495"
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64

將所表示的 UTC 時間轉換**struct** **tm**所表示的 UTC 時間**time_t**型別。

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
UTC 時間的指標**struct** **tm**轉換。

## <a name="return-value"></a>傳回值

類型的數量 **__time32_t**或是 **__time64_t**自 1970 年 1 月 1 日，以 Coordinated Universal Time (UTC) 午夜後經過的表示的秒數。 如果日期超出範圍 （請參閱 < 備註 > 一節） 或輸入無法解譯為有效的時間，傳回的值為-1。

## <a name="remarks"></a>備註

**_Mkgmtime32**並 **_mkgmtime64**函式轉換 UTC 時間 **__time32_t**或 **__time64_t**代表時間型別UTC。 若要將當地時間轉換為 UTC 時間，使用**mktime**， **_mktime32**，並 **_mktime64**改。

**_mkgmtime**是評估為內嵌函數 **_mkgmtime64**，以及**time_t**相當於 **__time64_t**。 如果您要強制編譯器將解譯**time_t**為舊的 32 位元**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 這因為您的應用程式可能會在 2038 年 1 月 18 日之後失敗，所以不建議使用 (32 位元的最大範圍**time_t**)，且不允許完全在 64 位元平台上。

結構傳入的時間將會變更，如下所示，在相同的方式如有變更與 **_mktime**函式： **tm_wday**並**tm_yday**新欄位設定為值的值計算**tm_mday**並**tm_year**。 指定時**tm**結構的時間，設定**tm_isdst**欄位設為：

- 零 (0)，以指出標準時間已生效。

- 大於 0 的值，以指出日光節約時間已生效。

- 小於 0 的值，使 C 執行階段程式庫程式碼計算標準時間或日光節約時間是否生效。

C 執行階段程式庫使用 TZ 環境變數來判斷正確的日光節約時間。 如果未設定 TZ，則會查詢作業系統以取得正確的地區日光節約時間行為。 **tm_isdst**  是必要的欄位。 如果未設定，其值為未定義和傳回值**mktime**無法預期。

範圍 **_mkgmtime32**函式是從 1970 年 1 月 1 日午夜 UTC 到 23:59:59 2038 年 1 月 18 日 UTC。 範圍 **_mkgmtime64**是從 1970 年 1 月 1 日午夜 UTC 到 23:59:59，3000 年 12 月 31 日 UTC。 範圍外的日期會導致傳回值為-1。 範圍 **_mkgmtime**取決於是否 **_USE_32BIT_TIME_T**定義。 如果未定義 （預設值） 的範圍是屬於 **_mkgmtime64**; 否則範圍會限制為 32 位元範圍 **_mkgmtime32**。

請注意， **gmtime**並**localtime**使用單一靜態配置的緩衝區來進行轉換。 如果您提供此緩衝區**mkgmtime**，先前的內容會遭到銷毀。

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
