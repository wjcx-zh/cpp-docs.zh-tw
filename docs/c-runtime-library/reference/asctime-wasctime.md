---
title: asctime、_wasctime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
dev_langs:
- C++
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b18edc9e61f7065fcac1fe6231012bd232ccc18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396192"
---
# <a name="asctime-wasctime"></a>asctime、_wasctime

轉換**tm**時間字元字串的結構。 這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

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

**asctime**讓指標回到字元字串結果。**_wasctime**寬字元字串結果傳回的指標。 沒有錯誤傳回值。

## <a name="remarks"></a>備註

這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

**Asctime**函式會將時間儲存為字元字串的結構的轉換。 *Timeptr*值通常取自呼叫**gmtime**或**localtime**，兩者都傳回的指標**tm**結構中所定義的時間。H.

|timeptr 成員|值|
|--------------------|-----------|
|**tm_hour**|午夜 (0-23) 的小時|
|**tm_isdst**|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，使用美國的規則。|
|**tm_mday**|月份 (1-31) 天數|
|**tm_min**|小時 (0-59) 之後的分鐘|
|**tm_mon**|月 (0-11。年 1 月 = 0）|
|**tm_sec**|分鐘 (0-59) 之後的秒數|
|**tm_wday**|(0-6; 週間日星期日 = 0）|
|**tm_yday**|年 (0 365; 中的日年 1 月 1 = 0)|
|**tm_year**|年份 (目前年份減去 1900 年)|

已轉換的字元字串也會根據當地時區設定調整。 如需設定本機時間的資訊，請參閱 [time](time-time32-time64.md)、[_ftime](ftime-ftime32-ftime64.md) 和 [localtime](localtime-localtime32-localtime64.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](tzset.md) 函式。

所產生的字串結果**asctime**包含完全 26 個字元，其格式`Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 **asctime**使用單一的靜態配置的緩衝區來保存傳回的字串。 每次呼叫此函式都會導致先前呼叫結果的終結。

**_wasctime**是寬字元版本的**asctime**。 **_wasctime**和**asctime**除此之外的行為相同。

這些函式會驗證它們的參數。 如果*timeptr*為 null 指標，或如果它包含超出範圍的值時，無效參數處理常式叫用時，所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則此函數會傳回**NULL**並設定**errno**至**EINVAL**。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> 或 \<wchar.h>|

## <a name="example"></a>範例

此程式會放在長整數的系統時間**aclock**，將它轉譯成結構**newtime** ，然後將它轉換成字串形式的輸出，使用**asctime**函式。

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
