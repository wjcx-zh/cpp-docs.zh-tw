---
title: ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64
ms.date: 11/04/2016
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
ms.openlocfilehash: ee802e9e6ddef839f08cf6dab6573f404328b2c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937764"
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

*sourceTime*<br/>
要轉換之預存時間的指標。

## <a name="return-value"></a>傳回值

字元字串結果的指標。 如果是下列情況，則會傳回**Null** ：

- *sourceTime*代表1970年1月1日午夜之前的日期（UTC）。

- 如果您使用 **_ctime32**或 **_Wctime32** ，而*SourceTime*代表23:59:59 年1月 18 2038 日之後的日期，則為 UTC。

- 如果您使用 **_ctime64**或 **_Wctime64** ，而*SourceTime*代表23:59:59 年12月 3000 31 日（UTC）之後的日期。

**ctime**是一個會評估為 **_ctime64**的內嵌函式，而**time_t**相當於 **__time64_t**。 如果您需要強制編譯器將**time_t**解讀為舊版32位**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 這麼做會導致**ctime**評估為 **_ctime32**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

## <a name="remarks"></a>備註

**Ctime**函數會將儲存為[time_t](../../c-runtime-library/standard-types.md)值的時間值轉換成字元字串。 *SourceTime*值通常是從呼叫[時間](time-time32-time64.md)取得，這會傳回自00:00:00 年1月1日（1970，國際標準時間（UTC））以來經過的秒數。 傳回值字串剛好包含 26 個字元，且具有以下格式：

```Output
Wed Jan 02 02:03:55 1980\n\0
```

使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 ('\n') 和 null 字元 ('\0') 佔用字串的最後兩個位置。

已轉換的字元字串也會根據當地時區設定調整。 如需有關設定當地時間和[_tzset](tzset.md)函式的詳細資訊，請參閱[time](time-time32-time64.md)、 [_ftime](ftime-ftime32-ftime64.md)和[localtime](localtime-localtime32-localtime64.md)函數，以取得定義時區環境和全域變數的詳細資訊。

對**ctime**的呼叫會修改**gmtime**和**localtime**函數所使用的單一靜態配置緩衝區。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。 **ctime**會與**asctime**函數共用靜態緩衝區。 因此，對**ctime**的呼叫會終結任何先前呼叫**asctime**、 **localtime**或**gmtime**的結果。

**_wctime**和 **_wctime64**是**ctime**和 **_ctime64**的寬字元版本;傳回寬字元字串的指標。 否則， **_ctime64**、 **_wctime**和 **_wctime64**的行為與**ctime**相同。

這些函式會驗證它們的參數。 如果*sourceTime*為 null 指標，或如果*sourceTime*值為負數，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回**Null** ，並將**Errno**設為**EINVAL**。

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
