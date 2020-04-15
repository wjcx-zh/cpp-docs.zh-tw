---
title: _strdate_s、_wstrdate_s
description: _strdate_s和_wstrdate_s是將當前日期放入緩衝區_strdate和_wstrdate函數的安全 CRT 版本。
ms.date: 4/2/2020
api_name:
- _strdate_s
- _wstrdate_s
- _o__strdate_s
- _o__wstrdate_s
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
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: b4d977ba3546eae17218c63b1786fd26c784d340
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359826"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s、_wstrdate_s

將目前的系統日期複製到緩衝區。 這些功能是_strdate的版本[,_wstrdate](strdate-wstrdate.md)具有[CRT 中安全功能中所述的安全](../../c-runtime-library/security-features-in-the-crt.md)增強功能。

## <a name="syntax"></a>語法

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*緩衝區*\
指向緩衝區的指標,用於放置格式化的日期字串。

*大小*\
緩衝區的大小(以字元單位為單位)。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果發生故障,返回值是錯誤代碼。 錯誤碼在 EERRNO.H 中定義，請參閱下表查看此函式產生的確切錯誤。 如需錯誤碼的詳細資訊，請參閱 [errno](../../c-runtime-library/errno-constants.md)。

## <a name="error-conditions"></a>錯誤條件

|*緩衝區*|*大小*|傳回|*緩衝區*的內容|
|--------------|------------------------|------------|--------------------------|
|**空**|(任何)|**埃因瓦爾**|未修改|
|非**NULL(** 指向有效緩衝區 )|0|**埃因瓦爾**|未修改|
|非**NULL(** 指向有效緩衝區 )|0 <*尺寸*< 9|**埃因瓦爾**|空字串|
|非**NULL(** 指向有效緩衝區 )|*大小*>= 9|0|目前的日期格式一如＜備註＞所指定|

## <a name="security-issues"></a>安全性問題

如果*大小*參數大於 9,則為*緩衝區*傳入無效的非 NULL 值會導致訪問衝突。

傳遞大於*緩衝區*實際大小*的值*會導致緩衝區溢出。

## <a name="remarks"></a>備註

這些函數提供了更安全的 **_strdate**和 **_wstrdate**版本。 **_strdate_s**函數將當前系統日期複製到*緩衝區*指向的緩衝區。 它的格式`mm/dd/yy`,`mm`其中 是兩位數的`dd`月份, 是兩位數的一`yy`天,是一年中的最後兩位數位。 例如，字串 `12/05/99` 代表 1999 年 12 月 5 日。 緩衝區必須至少為九個字元長。

**_wstrdate_s**是 **_strdate_s**的寬字元版本;**_wstrdate_s**的參數和返回值是寬字元字串。 除此之外，這些函式的行為相同。

當*緩衝區*是**NULL**指標,或者*大小*小於 9 個字元時,將呼叫無效的參數處理程式。 參數[驗證](../../c-runtime-library/parameter-validation.md)中對此進行了描述。 如果允許繼續執行,這些函數將返回 -1。 如果緩衝區為**NULL**或*大小*小於或等於 0,則它們將**errno**設置為**EINVAL。** 或者,如果*大小*小於 9,他們會將**errno**設置為**ERANGE。**

在C++,這些函數的使用通過範本重載簡化。 重載可以自動推斷緩衝區長度,從而無需指定*大小*參數。 而且,它們還可以用更新、更安全的對應函數自動替換不安全的函數。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>通用文字例程映射:

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> 或 \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>範例

請參閱 [time](time-time32-time64.md) 的範例。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)\
[asctime_s,_wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s,_localtime32_s,_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)\
[時間,_time32,_time64](time-time32-time64.md)\
[_tzset](tzset.md)
