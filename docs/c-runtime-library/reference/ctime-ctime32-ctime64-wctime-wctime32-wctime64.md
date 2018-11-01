---
title: ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64
ms.date: 11/04/2016
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: d1858a36c68a2ca5cedf70a1d74d5f250cbac8df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580816"
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64

將時間值轉換為字串並針對當地時區設定調整。 這些函式已有更安全的版本可用，請參閱 [ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)。

## <a name="syntax"></a>語法

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>參數

*sourceTime*<br/>
要轉換的預存時間的指標。

## <a name="return-value"></a>傳回值

字元字串結果的指標。 **NULL**會傳回：

- *sourceTime*代表 1970 年 1 月 1 日午夜 UTC 以前的日期。

- 如果您使用 **_ctime32**或是 **_wctime32**並*sourceTime*代表以後 23:59:59 2038 年 1 月 18 日 UTC 的日期。

- 如果您使用 **_ctime64**或是 **_wctime64**並*sourceTime*代表以後 23:59:59，3000 年 12 月 31 日 UTC 的日期。

**ctime**是內嵌函式，而它評估成 **_ctime64**並**time_t**相當於 **__time64_t**。 如果您要強制編譯器將解譯**time_t**為舊的 32 位元**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 如此一來，這會導致**ctime**評估為 **_ctime32**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

## <a name="remarks"></a>備註

**Ctime**函式會轉換為所儲存的時間值[time_t](../../c-runtime-library/standard-types.md)轉換為字元字串的值。 *SourceTime*值通常取自對[時間](time-time32-time64.md)，就會傳回午夜所經過的秒數 (00: 00:00) 1970 年 1 月 1 日國際標準時間 (UTC)。 傳回值字串剛好包含 26 個字元，且具有以下格式：

```Output
Wed Jan 02 02:03:55 1980\n\0
```

使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 ('\n') 和 null 字元 ('\0') 佔用字串的最後兩個位置。

已轉換的字元字串也會根據當地時區設定調整。 請參閱[時間](time-time32-time64.md)， [_ftime](ftime-ftime32-ftime64.md)，並[localtime](localtime-localtime32-localtime64.md)函式，如需設定當地時間和[_tzset](tzset.md)函式需定義時區環境及全域變數的詳細資料。

呼叫**ctime**修改所使用的單一靜態配置的緩衝區**gmtime**並**localtime**函式。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。 **ctime**共用靜態緩衝區**asctime**函式。 因此，呼叫**ctime**終結任何先前呼叫結果**asctime**， **localtime**，或**gmtime**。

**_wctime**並 **_wctime64**是寬字元版本**ctime**並 **_ctime64**; 傳回指向寬字元字串的指標。 否則，請 **_ctime64**， **_wctime**，並 **_wctime64**行為會和**ctime**。

這些函式會驗證它們的參數。 如果*sourceTime*為 null 指標，或如果*sourceTime*值是負數，這些函式叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md). 如果允許繼續執行，則函式會傳回**NULL**並設定**errno**來**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> 或 \<wchar.h>|
|**_wctime32**|\<time.h> 或 \<wchar.h>|
|**_wctime64**|\<time.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
