---
title: ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348241"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64

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

*來源時間*<br/>
指標到存儲的時間轉換。

## <a name="return-value"></a>傳回值

字元字串結果的指標。 **NULL**如果:

- *sourceTime*表示 1970 年 1 月 1 日午夜之前的日期,UTC。

- 如果您使用 **_ctime32**或 **_wctime32,** 並且*sourceTime*表示 2038 年 1 月 18 日 23:59:59 之後的日期,UTC。

- 如果您使用 **_ctime64**或 **_wctime64,** 並且*sourceTime*表示 23:59:59,3000 年 12 月 31 日 UTC 之後的日期。

**ctime**是一個內聯函數,它計算到 **_ctime64,time_t**等效於 **__time64_t。** **_ctime64** 如果需要強制編譯器將**time_t**解釋為舊的 32 位**time_t**,則可以定義 **_USE_32BIT_TIME_T**。 這樣做將導致**ctime**評估**到_ctime32**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

## <a name="remarks"></a>備註

**ctime**函數將儲存為[time_t](../../c-runtime-library/standard-types.md)值的時間值轉換為字串。 *sourceTime*值通常從調用[時間](time-time32-time64.md)獲得,該調用返回自 1970 年 1 月 1 日午夜 (00:00:00:00) 起經過的秒數,協調通用時間 (UTC)。 傳回值字串剛好包含 26 個字元，且具有以下格式：

```Output
Wed Jan 02 02:03:55 1980\n\0
```

使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 ('\n') 和 null 字元 ('\0') 佔用字串的最後兩個位置。

已轉換的字元字串也會根據當地時區設定調整。 有關配置本地時間和[_tzset](tzset.md)函數的詳細資訊,請參閱[時間](time-time32-time64.md)[、_ftime](ftime-ftime32-ftime64.md)和[本地時間](localtime-localtime32-localtime64.md)函數。

對**ctime**的呼叫修改了**gmtime**和**本地時間**函數使用的單個靜態分配的緩衝區。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。 **ctime**共用具有**asctime**函數的靜態緩衝區。 因此,對**ctime**的調用會破壞以前對**asctime、****本地時間**或**gmtime**的任何調用的結果。

**_wctime**和 **_wctime64**是**ctime**和 **_ctime64**的寬字元版本;返回指向寬字元字串的指標。 否則 **,_ctime64、_wctime**和 **_wctime64**行為與 **_wctime****ctime**相同。

這些函式會驗證它們的參數。 如果*sourceTime*是空指標,或者如果*sourceTime*值為負,則這些函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將傳回**NULL**並將**errno**設定為**EINVAL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
