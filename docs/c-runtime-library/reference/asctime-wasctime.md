---
title: asctime、_wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: bda14f3b6046378ad23148371f354bb910163d3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350476"
---
# <a name="asctime-_wasctime"></a>asctime、_wasctime

將**tm**時間結構轉換為字串。 這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

## <a name="syntax"></a>語法

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>參數

*timeptr*<br/>
時間/日期結構。

## <a name="return-value"></a>傳回值

**asctime**傳回指向字串結果的指標;**_wasctime**返回指向寬字元字串結果的指標。 沒有錯誤傳回值。

## <a name="remarks"></a>備註

這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

**asctime**函數將儲存為結構的時間轉換為字串。 *時間點*值通常從對**gmtime**或**本地時間的**調用中獲得,這兩個調用都會返回指向 TM**結構的**指標,該指標在「時代」中定義。H。

|timeptr 成員|值|
|--------------------|-----------|
|**tm_hour**|午夜起(0-23)以來的上班時間|
|**tm_isdst**|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，使用美國的規則。|
|**tm_mday**|月日 (1-31)|
|**tm_min**|一小時后幾分鐘 (0-59)|
|**tm_mon**|月(0-11;1 月 = 0)|
|**tm_sec**|一秒後秒 (0-59)|
|**tm_wday**|星期一(0-6;週日 = 0)|
|**tm_yday**|一年日(0-365;1 月 1 日 = 0)|
|**tm_year**|年份 (目前年份減去 1900 年)|

已轉換的字元字串也會根據當地時區設定調整。 如需設定本機時間的資訊，請參閱 [time](time-time32-time64.md)、[_ftime](ftime-ftime32-ftime64.md) 和 [localtime](localtime-localtime32-localtime64.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](tzset.md) 函式。

**asctime**產生的字串結果正好包含 26 個字元,並且具有`Wed Jan 02 02:03:55 1980\n\0`窗型 。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 **asctime**使用單個靜態分配的緩衝區來保存返回字串。 每次呼叫此函式都會導致先前呼叫結果的終結。

**_wasctime**是一個寬字元版本的**asctime。** **_wasctime**和**asctime**行為相同。

這些函式會驗證它們的參數。 如果*timeptr*是空指標,或者如果它包含範圍外的值,則調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回**NULL**並將**errno**設定到**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> 或 \<wchar.h>|

## <a name="example"></a>範例

此程式將系統時間置於長整數**aclock**中,將其轉換為結構**新時間**,然後將其轉換為字串形式以進行輸出,使用**asctime**函數。

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
