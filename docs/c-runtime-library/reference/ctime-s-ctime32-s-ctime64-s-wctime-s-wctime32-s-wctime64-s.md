---
title: ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
dev_langs:
- C++
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3f9c5e6d9d6f0d910decae904cbbd75d995a6c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404314"
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s

將時間值轉換為字串並針對當地時區設定調整。 這些是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [ctime、_ctime64、_wctime、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
必須足以容納 26 個字元。 字元字串結果時，指標或**NULL**如果：

- *sourceTime*代表之前 1970 年 1 月 1 日午夜 UTC 日期。

- 如果您使用 **_ctime32_s**或 **_wctime32_s**和*sourceTime*代表 23:59:59 2038 年 1 月 18 日，UTC 之後的日期。

- 如果您使用 **_ctime64_s**或 **_wctime64_s**和*sourceTime*代表 23:59:59，3000 年 12 月 31 日 UTC 之後的日期。

- 如果您使用 **_ctime_s**或 **_wctime_s**，這些函式是以先前的函式的包裝函式。 請參閱＜備註＞一節。

*numberOfElements*<br/>
緩衝區的大小。

*sourceTime*<br/>
預存時間的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果由於參數無效而失敗，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回錯誤碼。 錯誤碼是在 ERRNO.H 中定義；如需這些錯誤的清單，請參閱 [errno](../../c-runtime-library/errno-constants.md)。 下表顯示每個錯誤條件所擲回的實際錯誤碼。

## <a name="error-conditions"></a>錯誤狀況

|*buffer*|*numberOfElements*|*sourceTime*|Return|中的值*緩衝區*|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|任何|任何|**EINVAL**|未修改|
|不**NULL** （指向有效的記憶體）|0|任何|**EINVAL**|未修改|
|不**NULL**|0< 大小 < 26|任何|**EINVAL**|空字串|
|不**NULL**|>= 26|NULL|**EINVAL**|空字串|
|不**NULL**|>= 26|< 0|**EINVAL**|空字串|

## <a name="remarks"></a>備註

**Ctime_s**函式將儲存為時間值，轉換[time_t](../../c-runtime-library/standard-types.md)結構轉換為字元字串。 *SourceTime*值通常取自呼叫[時間](time-time32-time64.md)，它會傳回從午夜以來經過的秒數 (00: 00:00)、 1970 年 1 月 1 日國際標準時間 (UTC)。 傳回值字串剛好包含 26 個字元，且具有以下格式：

`Wed Jan 02 02:03:55 1980\n\0`

使用 24 小時制。 所有欄位都具有固定寬度。 新行字元 ('\n') 和 null 字元 ('\0') 佔用字串的最後兩個位置。

已轉換的字元字串也會根據當地時區設定調整。 請參閱[時間](time-time32-time64.md)， [_ftime](ftime-ftime32-ftime64.md)，和[localtime32_s](localtime-s-localtime32-s-localtime64-s.md)設定本地時間的資訊函式和[_tzset](tzset.md)如需定義時區環境和全域變數資訊的函式。

**_wctime32_s**和 **_wctime64_s**是寬字元版本 **_ctime32_s**和 **_ctime64_s**; 傳回寬字元字串的指標。 否則， **_ctime64_s**， **_wctime32_s**，和 **_wctime64_s**行為即會相同與 **_ctime32_s**。

**ctime_s**是內嵌函式評估為 **_ctime64_s**和**time_t**相當於 **__time64_t**。 如果您要強制編譯器將解譯**time_t**為舊的 32 位元**time_t**，您可以定義 **_USE_32BIT_TIME_T**。 如此一來，這會導致**ctime_s**評估為 **_ctime32_s**。 建議您不要這樣做，原因是您的應用程式可能會在 2038 年 1 月 18 日後失敗，且在 64 位元平台上不允許這種定義。

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**ctime_s**， **_ctime32_s**， **_ctime64_s**|\<time.h>|
|**_wctime_s**， **_wctime32_s**， **_wctime64_s**|\<time.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
