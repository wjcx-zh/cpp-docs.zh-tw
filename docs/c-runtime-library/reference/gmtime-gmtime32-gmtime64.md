---
title: gmtime、_gmtime32、_gmtime64
description: Gmtime、_gmtime32 和 _gmtime64 的 API 參考;這會將 time_t 值轉換為 tm 結構。
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: b3dd09e828b972f05a4c45c30ebc3e5edb68f551
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556459"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime、_gmtime32、_gmtime64

將 **time_t** 時間值轉換為 **tm** 結構。 這些函式有更安全的版本可供使用；請參閱 [gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)。

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

[tm](../../c-runtime-library/standard-types.md) 類型之結構的指標。 傳回之結構的欄位會保留 *sourceTime* 引數的評估值（UTC），而不是當地時間。 每個結構欄位都屬於類型，如下所示 **`int`** ：

|欄位|描述|
|-|-|
|**tm_sec**|分鐘之後的秒數 (0-59) 。|
|**tm_min**|小時之後的分鐘 (0-59) 。|
|**tm_hour**|自午夜 (0-23) 之後的時數。|
|**tm_mday**|月中的日 (1-31) 。|
|**tm_mon**|月 (0-11;1月 = 0) 。|
|**tm_year**|年份 (目前年份減去 1900)。|
|**tm_wday**|周中的日 (0-6;星期日 = 0) 。|
|**tm_yday**|年中的日 (0-365;1月1日 = 0) 。|
|**tm_isdst**|**Gmtime**一律為0。|

32位和64位版本的 **gmtime**、 [mktime](mktime-mktime32-mktime64.md)、 [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)和 [localtime](localtime-localtime32-localtime64.md) 都在轉換時，每個執行緒都會使用一個通用的 **tm** 結構。 每次呼叫這些函式的其中之一時，會終結任何先前呼叫的結果。 如果 *sourceTime* 代表在1970年1月1日午夜之前的日期， **Gmtime** 會傳回 **Null**。 不會傳回錯誤。

使用 **__time64_t**結構的 **_gmtime64**，可讓日期以23:59:59 年12月31日 3000 utc 為單位來表示，而 **_gmtime32**只代表日期到23:59:59 年1月18日至2038的 utc。 1970 年 1 月 1 日午夜是這兩個函式的日期範圍下限。

**gmtime**是評估為 **_gmtime64**的內嵌函式，除非已定義 **_USE_32BIT_TIME_T** ，否則**time_t**相當於 **__time64_t** 。 如果您必須強制編譯器將 **time_t** 解讀為舊的32位 **time_t**，您可以定義 **_USE_32BIT_TIME_T**，但是這樣做會使 **gmtime** 以內嵌方式寫入 **_gmtime32** ，且 **time_t** 會定義為 **__time32_t**。 我們建議您不要這麼做，因為 64 位元平台上不允許這種定義，而且在任何情況下，您的應用程式可能會在 2038 年 1 月 18 日之後失敗。

這些函式會驗證它們的參數。 如果 *sourceTime* 為 null 指標，或如果 *sourceTime* 值為負數，則這些函式會叫用不正確參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回 **Null** ，並將 **Errno** 設定為 **EINVAL**。

## <a name="remarks"></a>備註

**_Gmtime32**函式會細分*sourceTime*值，並將它儲存在靜態配置的**tm**類型結構中，並以 .h 定義。 *SourceTime*的值通常是從運行[時間](time-time32-time64.md)函式的呼叫所取得。

> [!NOTE]
> 在大部分情況下，目標環境會嘗試判斷日光節約時間是否生效。 C 執行階段程式庫會假定使用美國的規則，以實作日光節約時間 (DST) 的計算。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的 C 標頭|必要的 C++ 標頭|
|-------------|---------------------|-|
|**gmtime**、 **_gmtime32**、 **_gmtime64**|\<time.h>|\<ctime> 或 \<time.h>|

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
[localtime，_localtime32，_localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
