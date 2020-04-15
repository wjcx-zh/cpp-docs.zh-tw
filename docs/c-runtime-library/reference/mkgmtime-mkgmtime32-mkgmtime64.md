---
title: _mkgmtime、_mkgmtime32、_mkgmtime64
description: 描述 _mkgmtime、_mkgmtime32 和 _mkgmtime64 C 運行時庫函數,並舉例說明如何使用它們。
ms.date: 4/2/2020
api_name:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
- _o__mkgmtime32
- _o__mkgmtime64
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
ms.openlocfilehash: e8b3170fc0413a878777035fd76aac5eefa7b6bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338766"
---
# <a name="_mkgmtime-_mkgmtime32-_mkgmtime64"></a>_mkgmtime、_mkgmtime32、_mkgmtime64

將由**結構****tm**表示的UTC時間轉換為由**time_t**類型表示的UTC時間。

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

*時間分器*\
指向 UTC 時間的指標,作為要轉換**的結構** **tm。**

## <a name="return-value"></a>傳回值

表示自 1970 年 1 月 1 日午夜以來在協調通用時間 (UTC) 中經過的秒數的 **__time32_t**或 **__time64_t**數量。 如果日期超過範圍(請參閱備註部分),或者輸入不能解釋為有效時間,則返回值為 -1。

## <a name="remarks"></a>備註

**_mkgmtime32**和 **_mkgmtime64**函數將 UTC 時間轉換為表示 UTC 中時間的 **__time32_t**或 **__time64_t**類型。 要將本地時間轉換為 UTC 時間,請使用**mktime、_mktime32**和 **_mktime64。** **_mktime32**

**_mkgmtime**是一個內聯函數,用於計算到 **_mkgmtime64,time_t****__time64_t**等效**time_t**於 __time64_t 。 如果需要強制編譯器將**time_t**解釋為舊的 32 位**time_t**,則可以定義 **_USE_32BIT_TIME_T**。 我們不推薦它,因為您的應用程式可能在 2038 年 1 月 18 日之後失敗,32 位**的最大範圍time_t**。 在 64 位平臺上根本不允許它。

傳入的時間結構按如下方式更改,其方式與 **_mktime**函數更改的方式相同 **:tm_wday**和**tm_yday**欄位設置為基於**tm_mday**和**tm_year**的值的新值。 由於時間假定為**UTC,因此**tm_isdst欄位將被忽略。

**_mkgmtime32**功能的範圍是從 1970 年 1 月 1 日午夜到 UTC 到 2038 年 1 月 18 日 23:59:59,UTC。 **_mkgmtime64**範圍為 1970 年 1 月 1 日午夜、UTC 至 23:59:59、12 月 31 日、3000 年 UTC。 範圍外日期會導致返回值 -1。 **_mkgmtime**範圍取決於是否定義了 **_USE_32BIT_TIME_T。** 如果未定義它(預設值)時,範圍與 **_mkgmtime64**相同。 否則,範圍將限制為**32**位_mkgmtime32範圍。

**gmtime**和**本地時間**都使用公共靜態緩衝區進行轉換。 如果向 **_mkgmtime**提供此緩衝區,則銷毀前面的內容。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="examples"></a>範例

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

```Output
Seconds since midnight, January 1, 1970
My time: 1171588492
GM time (UTC): 1171588492

Local Time: Thu Feb 15 17:14:52 2007

Greenwich Mean Time: Fri Feb 16 01:14:52 2007
```

下面的示例顯示了 _mkgmtime 如何填充不完整**的結構。** 它計算一周和一年中的一天的值。

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

```Output
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003
t.tm_yday = 0
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003
t.tm_yday = 42
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)\
[asctime, _wasctime](asctime-wasctime.md)\
[asctime_s,_wasctime_s](asctime-s-wasctime-s.md)\
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s,_localtime32_s,_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[time、_time32、_time64](time-time32-time64.md)
