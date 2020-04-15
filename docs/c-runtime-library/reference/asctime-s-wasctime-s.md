---
title: asctime_s、_wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
ms.openlocfilehash: 52391eb1237e4c1d7ef320dacd211b603a21ab8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334217"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s、_wasctime_s

將**tm**時間結構轉換為字串。 這是如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [asctime、_wasctime](asctime-wasctime.md) 版本。

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

*緩衝區*<br/>
指向緩衝區的指標,用於存儲字串結果。 此函數假定指向具有*由 NumberOfElements*指定的大小的有效記憶體位置的指標。

*元素數*<br/>
用於存儲結果的緩衝區的大小。

*tm 來源*<br/>
時間/日期結構。 此函數假指向有效結構**tm**物件的**指標**。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，傳回值為錯誤碼。 錯誤碼於 ERRNO.H 中定義。 如需詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。 下表顯示每個錯誤條件所傳回的實際錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*緩衝區*|*元素數*|*tm 來源*|傳回|*緩衝區*中的值|
|--------------|------------------------|----------|------------|-----------------------|
|**空**|任意|任意|**埃因瓦爾**|未修改|
|**非 NULL(** 指向有效記憶體 )|0|任意|**埃因瓦爾**|未修改|
|非**NULL**|0< 大小 < 26|任意|**埃因瓦爾**|空字串|
|非**NULL**|>= 26|**空**|**埃因瓦爾**|空字串|
|非**NULL**|>= 26|無效的時間結構或超出時間元件值的範圍|**埃因瓦爾**|空字串|

> [!NOTE]
> **wasctime_s**的錯誤條件與**asctime_s**類似,但大小限制以文字度量。

## <a name="remarks"></a>備註

**asctime**函數將儲存為結構的時間轉換為字串。 *tmSource*值通常從對**gmtime**或**本地時間的**調用中獲得。 這兩個函數都可用於填充**TM**結構,如《時代》中定義的那樣。H。

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

已轉換的字元字串也會根據當地時區設定調整。 如需設定本機時間的資訊，請參閱 [time、_time32、_time64](time-time32-time64.md)、[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 及 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](tzset.md) 函式。

**asctime_s**產生的字串結果正好包含 26 個字元,並且具有`Wed Jan 02 02:03:55 1980\n\0`窗體 。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 當作第二個參數傳入的值至少應有這麼大。 如果較少,將返回錯誤代碼**EINVAL。**

**_wasctime_s**是**asctime_s**的寬字元版本。 **_wasctime_s**和**asctime_s**行為相同。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

在 C++ 中，使用這些函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 或 \<wchar.h>|

## <a name="security"></a>安全性

如果緩衝區指標不是**NULL,** 並且指標不指向有效的緩衝區,則函數將覆蓋位置的任何內容。 這也會導致存取違規。

如果傳入的大小引數大於緩衝區的實際大小，就會發生[緩衝區滿溢](/windows/win32/SecBP/avoiding-buffer-overruns)。

## <a name="example"></a>範例

此程式將系統時間置於長整數**aclock**中,將其轉換為結構**新時間**,然後將其轉換為字串形式以進行輸出,使用**asctime_s**函數。

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

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
