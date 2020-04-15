---
title: gmtime_s、_gmtime32_s、_gmtime64_s
ms.date: 4/2/2020
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
- _o__gmtime32_s
- _o__gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: e73d2d3cca852b657631361d8271bec7f9c86ac5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344085"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s、_gmtime32_s、_gmtime64_s

將時間值轉換為**tm**結構。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>參數

*tmDest*<br/>
指向[tm](../../c-runtime-library/standard-types.md)結構的指標。 返回結構的欄位在UTC而不是本地時間保存*計時器*參數的計算值。

*來源時間*<br/>
預存時間的指標。 時間以國際標準時間 1970 年 1 月 1 日 (UTC) 午夜 (00: 00:00) 以來經過的秒代表。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤代碼在 Errno.h 中定義;有關這些錯誤的清單,請參閱[errno](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>錯誤狀況

|*tmDest*|*來源時間*|傳回|以*tmD 最大值*|
|-----------|------------|------------|--------------------|
|**空**|任意|**埃因瓦爾**|未修改。|
|**非 NULL(** 指向有效記憶體 )|**空**|**埃因瓦爾**|所有的欄位設定為 -1。|
|非**NULL**|< 0|**埃因瓦爾**|所有的欄位設定為 -1。|

在前兩個錯誤條件的情況下，叫用了無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,這些函數將**errno**設定為**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

**_gmtime32_s**函數分解*源時間*值並將其存儲在在 Time.h 中定義的**tm**類型結構中。 結構的位址以*tmDest*形式傳遞。 *源時間*的值通常從對[時間](time-time32-time64.md)函數的調用中獲得。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。 C 執行階段程式庫會假定使用美國的規則，以實作日光節約時間的計算。

每個結構欄位的類型**為 int,** 如下表所示。

|欄位|描述|
|-|-|
|**tm_sec**|一分鐘后秒 (0 - 59)。|
|**tm_min**|一小時后幾分鐘 (0 - 59)。|
|**tm_hour**|午夜起(0 - 23日)的上班時間。|
|**tm_mday**|月日(1 - 31)。|
|**tm_mon**|月 (0 - 11;1 月 = 0)。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|星期一(0 - 6;周日 = 0)。|
|**tm_yday**|一年中的日子(0 - 365;1 月 1 = 0)。|
|**tm_isdst**|始終為**0**gmtime_s 。|

**_gmtime64_s**() 使用 **__time64_t**結構,允許日期在 23:59:59,3000 年 12 月 31 日(UTC)前表示;而**gmtime32_s**僅表示 2038 年 1 月 18 日 23:59:59,UTC 的日期。 1970 年 1 月 1 日午夜是所有這兩個函式的日期範圍下限。

**gmtime_s**是一個內聯函數,它計算到 **_gmtime64_s,time_t**相當於 **__time64_t。** **time_t** 如果需要強制編譯器將**time_t**解釋為舊的 32 位**time_t**,則可以定義 **_USE_32BIT_TIME_T**。 這樣做將導致**gmtime_s_gmtime32_s。** **_gmtime32_s** 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**gmtime_s**, **_gmtime32_s**, **_gmtime64_s**|\<time.h>|\<ctime\<> 或時間.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
