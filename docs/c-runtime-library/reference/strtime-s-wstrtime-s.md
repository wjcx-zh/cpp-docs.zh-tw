---
title: _strtime_s、_wstrtime_s
ms.date: 4/2/2020
api_name:
- _wstrtime_s
- _strtime_s
- _o__strtime_s
- _o__wstrtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: 771dfdb6bd8035fe8683d62d52b3b4980ecda215
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316946"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s、_wstrtime_s

將目前的時間複製到緩衝區。 這些版本的 [_strtime、_wstrtime](strtime-wstrtime.md) 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*緩衝區*<br/>
長度至少為 10 個位元組的緩衝區內會寫入時間。

*元素數*<br/>
緩衝區的大小。

## <a name="return-value"></a>傳回值

如果成功，則為零。

如果發生錯誤，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果失敗，傳回的值會是錯誤碼。 錯誤碼在 EERRNO.H 中定義，請參閱下表查看此函式產生的確切錯誤。 如需錯誤碼的詳細資訊，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>錯誤狀況

|*緩衝區*|*元素數*|傳回|*緩衝區*的內容|
|--------------|------------------------|------------|--------------------------|
|**空**|(任何)|**埃因瓦爾**|未修改|
|非**NULL(** 指向有效緩衝區 )|0|**埃因瓦爾**|未修改|
|非**NULL(** 指向有效緩衝區 )|0 < 大小 < 9|**埃因瓦爾**|空字串|
|非**NULL(** 指向有效緩衝區 )|大小 > 9|0|目前的時間格式一如＜備註＞所指定|

## <a name="security-issues"></a>安全性問題

如果*數量OfElements*參數大於9,則傳入緩衝區無效的非**NULL**值將導致訪問衝突。

傳遞大於緩衝區實際大小的*數量元素的值*將導致緩衝區溢出。

## <a name="remarks"></a>備註

這些函數提供了更安全的[_strtime](strtime-wstrtime.md)版本,_wstrtime。 [_wstrtime](strtime-wstrtime.md) **_strtime_s**函數將當前本地時間複製到*時間點*指向的緩衝區中。 時間格式為**hh:mm:ss,** 其中**hh**是兩位數位,以 24 小時表示法表示小時 **,mm**是兩位數位,表示超過小時數的分鐘數 **,ss**是表示秒的兩位數位。 例如,字串**18:23:44**表示下午 6 點經過 23 分鐘 44 秒。 緩衝區必須至少有 9 個位元組長，實際大小由第二個參數指定。

**_wstrtime**是 **_strtime**的寬字元版本;**_wstrtime**的參數和返回值是寬字元字串。 除此之外，這些函式的行為相同。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<time.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
