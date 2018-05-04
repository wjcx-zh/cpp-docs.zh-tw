---
title: asctime_s、_wasctime_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
dev_langs:
- C++
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4300d5fdab43cf4d22cf4e1fdee790f9d06d00d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="asctimes-wasctimes"></a>asctime_s、_wasctime_s

轉換**tm**時間字元字串的結構。 這是如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [asctime、_wasctime](asctime-wasctime.md) 版本。

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
若要將字元字串的結果儲存緩衝區的指標。 此函式所指定的大小假設有效的記憶體位置的指標*numberOfElements*。

*numberOfElements*<br/>
用來儲存結果的緩衝區大小。

*tmSource*<br/>
時間/日期結構。 此函式會假設是有效的指標**結構** **tm**物件。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，傳回值為錯誤碼。 錯誤碼於 ERRNO.H 中定義。 如需詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。 下表顯示每個錯誤條件所傳回的實際錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*buffer*|*numberOfElements*|*tmSource*|Return|中的值*緩衝區*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|任何|任何|**EINVAL**|未修改|
|不**NULL** （指向有效的記憶體）|0|任何|**EINVAL**|未修改|
|不**NULL**|0< 大小 < 26|任何|**EINVAL**|空字串|
|不**NULL**|>= 26|**NULL**|**EINVAL**|空字串|
|不**NULL**|>= 26|無效的時間結構或超出時間元件值的範圍|**EINVAL**|空字串|

> [!NOTE]
> 錯誤條件**wasctime_s**類似於**asctime_s**與例外狀況的大小限制為測量單位的文字。

## <a name="remarks"></a>備註

**Asctime**函式會將時間儲存為字元字串的結構的轉換。 *TmSource*值通常取自呼叫**gmtime**或**localtime**。 這兩個函數可以用來填入**tm**結構所定義的時間。H.

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

已轉換的字元字串也會根據本機時區設定調整。 如需設定本機時間的資訊，請參閱 [time、_time32、_time64](time-time32-time64.md)、[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) 及 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) 函式；如需定義時區環境及全域變數的資訊，請參閱 [_tzset](tzset.md) 函式。

所產生的字串結果**asctime_s**包含完全 26 個字元，其格式`Wed Jan 02 02:03:55 1980\n\0`。 使用 24 小時制。 所有欄位都具有固定寬度。 新行字元和 Null 字元佔用字串的最後兩個位置。 當作第二個參數傳入的值至少應有這麼大。 如果是小於錯誤碼， **EINVAL**，將會傳回。

**_wasctime_s**是寬字元版本的**asctime_s**。 **_wasctime_s**和**asctime_s**除此之外的行為相同。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> 或 \<wchar.h>|

## <a name="security"></a>安全性

如果緩衝區指標不是**NULL**和指標不指向有效的緩衝區、 函式將會覆寫，不論是位置。 這也會導致存取違規。

如果傳入的大小引數大於緩衝區的實際大小，就會發生[緩衝區滿溢](http://msdn.microsoft.com/library/windows/desktop/ms717795)。

## <a name="example"></a>範例

此程式會放在長整數的系統時間**aclock**，將它轉譯成結構**newtime** ，然後將它轉換成字串形式的輸出，使用**asctime_s**函式。

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
[_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
