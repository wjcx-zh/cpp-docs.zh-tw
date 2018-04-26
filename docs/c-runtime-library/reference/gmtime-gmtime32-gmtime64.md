---
title: gmtime、_gmtime32、_gmtime64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
dev_langs:
- C++
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df2f7cc9f8bf6451ce8671b66c07fc5c3f06420d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="gmtime-gmtime32-gmtime64"></a>gmtime、_gmtime32、_gmtime64

將轉換**time_t**時間值以**tm**結構。 這些函式有更安全的版本可供使用；請參閱 [gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)。

## <a name="syntax"></a>語法

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>參數

*sourceTime*<br/>
預存時間的指標。 時間以國際標準時間 1970 年 1 月 1 日 (UTC) 午夜 (00: 00:00) 以來經過的秒代表。

## <a name="return-value"></a>傳回值

[tm](../../c-runtime-library/standard-types.md) 類型之結構的指標。 傳回結構的欄位保存的評估的值*sourceTime*引數以 utc 格式，而不是以本地時間。 每個結構欄位屬於類型**int**、，如下所示：

|欄位|描述|
|-|-|
|**tm_sec**|分鐘之後的秒數 (0-59)。|
|**tm_min**|小時之後的分鐘 (0-59)。|
|**tm_hour**|從午夜開始的小時 (0-23)。|
|**tm_mday**|日期的月份 (1-31)。|
|**tm_mon**|月 (0-11。年 1 月 = 0）。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|一週天數 (0-6;星期日 = 0）。|
|**tm_yday**|年中的日 (0-365;年 1 月 1 = 0)。|
|**tm_isdst**|永遠為 0 的**gmtime**。|

這兩個 32 位元和 64 位元版本的**gmtime**， [mktime](mktime-mktime32-mktime64.md)， [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)，和[localtime](localtime-localtime32-localtime64.md)都使用一個通用**tm**每個執行緒來進行轉換的結構。 每次呼叫這些函式的其中之一時，會終結任何先前呼叫的結果。 如果*sourceTime*代表日期 1970 年 1 月 1 日的午夜之前**gmtime**傳回**NULL**。 不會傳回錯誤。

**_gmtime64**，它會使用 **__time64_t**結構時，請啟用到 23:59:59，3000 年 12 月 31 日 UTC，透過設定來表示日期，而 **_gmtime32**只代表 23:59:59 之間的日期2038 年 1 月 18 日，UTC。 1970 年 1 月 1 日午夜是這兩個函式的日期範圍下限。

**gmtime**是內嵌函式評估為 **_gmtime64**，和**time_t**相當於 **__time64_t**除非 **_USE_32BIT_TIME_T**定義。 如果您必須強制編譯器將解譯**time_t**為舊的 32 位元**time_t**，您可以定義 **_USE_32BIT_TIME_T**，但是，因此原因**gmtime**要內嵌至 **_gmtime32**和**time_t**定義為 **__time32_t**。 我們建議您不要這麼做，因為 64 位元平台上不允許這種定義，而且在任何情況下，您的應用程式可能會在 2038 年 1 月 18 日之後失敗。

這些函式會驗證它們的參數。 如果*sourceTime*為 null 指標，或如果*sourceTime*值為負數，這些函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行，函式會傳回**NULL**並設定**errno**至**EINVAL**。

## <a name="remarks"></a>備註

**_Gmtime32**函式會細分*sourceTime*值，並將它儲存在類型的靜態配置結構**tm**，已定義的時間。H. 值*sourceTime*通常取自呼叫[時間](time-time32-time64.md)函式。

> [!NOTE]
> 在大部分情況下，目標環境會嘗試判斷日光節約時間是否生效。 C 執行階段程式庫會假定使用美國的規則，以實作日光節約時間 (DST) 的計算。

## <a name="requirements"></a>需求

|常式|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**gmtime**， **_gmtime32**， **_gmtime64**|\<time.h>|\<ctime > 或\<h >|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
