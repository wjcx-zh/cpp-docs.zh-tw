---
title: gmtime_s、_gmtime32_s、_gmtime64_s
ms.date: 11/04/2016
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
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
ms.openlocfilehash: bcfc512022393c6a3e8a9cd97efe96d03b4877ab
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954835"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s、_gmtime32_s、_gmtime64_s

將時間值轉換成**tm**結構。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md) 版本。

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
[Tm](../../c-runtime-library/standard-types.md)結構的指標。 傳回之結構的欄位會以 UTC 而非當地時間來保存*計時器*引數的評估值。

*sourceTime*<br/>
預存時間的指標。 時間以國際標準時間 1970 年 1 月 1 日 (UTC) 午夜 (00: 00:00) 以來經過的秒代表。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義；如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-constants.md)。

### <a name="error-conditions"></a>錯誤狀況

|*tmDest*|*sourceTime*|Return|*TmDest*中的值|
|-----------|------------|------------|--------------------|
|**NULL**|any|**EINVAL**|未修改。|
|Not **Null** （指向有效的記憶體）|**NULL**|**EINVAL**|所有的欄位設定為 -1。|
|非**Null**|< 0|**EINVAL**|所有的欄位設定為 -1。|

在前兩個錯誤狀況的情況下，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 這些函式會將**errno**設定為**EINVAL** , 並傳回**EINVAL**。

## <a name="remarks"></a>備註

**_Gmtime32_s**函式會細分*sourceTime*值，並將它儲存在以 Time .h 定義的類型**tm**結構中。 結構的位址會以*tmDest*傳遞。 *SourceTime*的值通常是從[time](time-time32-time64.md)函數的呼叫取得。

> [!NOTE]
> 目標環境應該嘗試判斷日光節約時間是否生效。 C 執行階段程式庫會假定使用美國的規則，以實作日光節約時間的計算。

每個結構欄位的類型為**int**，如下表所示。

|欄位|描述|
|-|-|
|**tm_sec**|分鐘後的秒數（0-59）。|
|**tm_min**|小時之後的分鐘（0-59）。|
|**tm_hour**|午夜後的小時（0-23）。|
|**tm_mday**|月中的日（1-31）。|
|**tm_mon**|月份（0-11;1月 = 0）。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|周中的日（0-6;星期日 = 0）。|
|**tm_yday**|年中的日（0-365;1月1日 = 0）。|
|**tm_isdst**|**Gmtime_s**一律為0。|

使用 **__time64_t**結構的 **_gmtime64_s**，可讓日期以23:59:59 年12月31日3000，UTC 表示。**gmtime32_s**只代表日期到23:59:59 年1月 18 2038 日，UTC。 1970 年 1 月 1 日午夜是所有這兩個函式的日期範圍下限。

**gmtime_s**是評估為 **_gmtime64_s**的內嵌函式，而**time_t**相當於 **__time64_t**。 如果您需要強制編譯器將**time_t**解讀為舊版32位**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 這麼做會使**gmtime_s**在 **_gmtime32_s**中。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

## <a name="requirements"></a>需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**gmtime_s**、 **_gmtime32_s**、 **_gmtime64_s**|\<time.h>|\<ctime > 或\<time. h >|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
