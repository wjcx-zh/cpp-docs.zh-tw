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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 00c6be8ee409d76b80d323102950f8c1d6420ba3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909431"
---
# <a name="asctime-_wasctime"></a>asctime、_wasctime

將**tm**時間結構轉換成字元字串。 這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

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

**asctime**會傳回字元字串結果的指標;**_wasctime**會傳回寬字元字串結果的指標。 沒有錯誤傳回值。

## <a name="remarks"></a>備註

這些函式有更安全的版本可用，請參閱 [asctime_s、_wasctime_s](asctime-s-wasctime-s.md)。

**Asctime**函數會將儲存為結構的時間轉換為字元字串。 *Timeptr*值通常是從呼叫**gmtime**或**localtime**取得，這兩種方式都會傳回以時間定義的**tm**結構的指標。H.

|timeptr 成員|值|
|--------------------|-----------|
|**tm_hour**|午夜後的小時（0-23）|
|**tm_isdst**|若日光節約時間已生效則為正值；如果日光節約時間沒有作用則為 0。如果日光節約時間的狀態是未知，則為負值。 C 執行階段程式庫會在實作日光節約時間 (DST) 的計算時，使用美國的規則。|
|**tm_mday**|月中的日（1-31）|
|**tm_min**|小時後的分鐘數（0-59）|
|**tm_mon**|月份（0-11;1月 = 0）|
|**tm_sec**|分鐘後的秒數（0-59）|
|**tm_wday**|周中的日（0-6;星期日 = 0）|
|**tm_yday**|年中的日（0-365;1月1日 = 0）|
|**tm_year**|年份 (目前年份減去 1900 年)|

已轉換的字元字串也會根據當地時區設定調整。 如需設定本機時間的資訊，請參閱 [time](time-time32-time64.md)、[_ftime](ftime-ftime32-ftime64.md) 和 [localtime](localtime-localtime32-localtime64.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](tzset.md) 函式。

**Asctime**所產生的字串結果只包含26個字元，且的`Wed Jan 02 02:03:55 1980\n\0`格式為。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 **asctime**會使用以靜態方式配置的單一緩衝區來保存傳回字串。 每次呼叫此函式都會導致先前呼叫結果的終結。

**_wasctime**是**asctime**的寬字元版本。 **_wasctime**和**asctime**的行為相同。

這些函式會驗證它們的參數。 如果*timeptr*為 null 指標，或包含超出範圍的值，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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

這個程式會將系統時間放在長整數**aclock**中，將它轉譯成結構**newtime** ，然後使用**asctime**函式將它轉換成字串格式以進行輸出。

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
