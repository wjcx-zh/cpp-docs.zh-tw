---
title: asctime_s、_wasctime_s
ms.date: 11/04/2016
api_name:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 1cd2a15db0a27dedd88b9abf24b98d338515c949
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624790"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s、_wasctime_s

將**tm**時間結構轉換成字元字串。 這是如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [asctime、_wasctime](asctime-wasctime.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
緩衝區的指標，用來儲存字元字串結果。 此函式會假設具有*numberOfElements*所指定大小之有效記憶體位置的指標。

*numberOfElements*<br/>
用來儲存結果的緩衝區大小。

*tmSource*<br/>
時間/日期結構。 此函式會假設有效**結構** **tm**物件的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，傳回值為錯誤碼。 錯誤碼於 ERRNO.H 中定義。 如需詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。 下表顯示每個錯誤條件所傳回的實際錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*buffer*|*numberOfElements*|*tmSource*|Return|*Buffer*中的值|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|Any|Any|**EINVAL**|未修改|
|Not **Null** （指向有效的記憶體）|0|Any|**EINVAL**|未修改|
|非**Null**|0< 大小 < 26|Any|**EINVAL**|空字串|
|非**Null**|>= 26|**NULL**|**EINVAL**|空字串|
|非**Null**|>= 26|無效的時間結構或超出時間元件值的範圍|**EINVAL**|空字串|

> [!NOTE]
> **Wasctime_s**的錯誤情況類似**asctime_s** ，但大小限制是以單字來測量的例外狀況。

## <a name="remarks"></a>備註

**Asctime**函數會將儲存為結構的時間轉換為字元字串。 *TmSource*值通常是從**gmtime**或**localtime**的呼叫取得。 這兩個函式可以用來填滿**tm**結構，如時間所定義。H.

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

已轉換的字元字串也會根據本機時區設定調整。 如需設定本機時間的資訊，請參閱 [time、_time32、_time64](time-time32-time64.md)、[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 及 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](tzset.md) 函式。

**Asctime_s**所產生的字串結果只包含26個字元，且格式為 `Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 當作第二個參數傳入的值至少應有這麼大。 如果較少，則會傳回錯誤碼**EINVAL**。

**_wasctime_s**是寬字元版本的**asctime_s**。 相反地， **_wasctime_s**和**asctime_s**的行為相同。

這些函式的 debug 程式庫版本會先以0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 或 \<wchar.h>|

## <a name="security"></a>安全性

如果緩衝區指標不是**Null** ，而且指標並未指向有效的緩衝區，則函式會覆寫位置上的任何內容。 這也會導致存取違規。

如果傳入的大小引數大於緩衝區的實際大小，就會發生[緩衝區滿溢](/windows/win32/SecBP/avoiding-buffer-overruns)。

## <a name="example"></a>範例

這個程式會將系統時間放在長整數**aclock**中，將它轉譯成結構**newtime** ，然後使用**asctime_s**函式，將它轉換成字串格式以進行輸出。

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
