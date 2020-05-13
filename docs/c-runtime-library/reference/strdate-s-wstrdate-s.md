---
title: _strdate_s、_wstrdate_s
description: _strdate_s 和 _wstrdate_s 是安全 CRT 版本的 _strdate，以及將目前日期放在緩衝區中的 _wstrdate 函數。
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7fe8d682ab515d5a11e90f0c26e956725644806e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916908"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s、_wstrdate_s

將目前的系統日期複製到緩衝區。 這些函式是 _strdate 的版本[，_wstrdate](strdate-wstrdate.md)具有[CRT 中的安全性功能中](../../c-runtime-library/security-features-in-the-crt.md)所述的安全性增強功能。

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
要放置格式化日期字串之緩衝區的指標。

*容量*\
緩衝區的大小（以字元為單位）。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果發生失敗，則傳回值為錯誤碼。 錯誤碼在 EERRNO.H 中定義，請參閱下表查看此函式產生的確切錯誤。 如需錯誤碼的詳細資訊，請參閱 [errno](../../c-runtime-library/errno-constants.md)。

## <a name="error-conditions"></a>錯誤條件

|*緩衝區*|*size*|傳回|*緩衝區*的內容|
|--------------|------------------------|------------|--------------------------|
|**Null**|(任何)|**EINVAL**|未修改|
|Not **Null** （指向有效的緩衝區）|0|**EINVAL**|未修改|
|Not **Null** （指向有效的緩衝區）|0 <*大小*< 9|**EINVAL**|空字串|
|Not **Null** （指向有效的緩衝區）|*大小*>= 9|0|目前的日期格式一如＜備註＞所指定|

## <a name="security-issues"></a>安全性問題

如果*size*參數大於9，傳入不正確*緩衝區*非 Null 值會造成存取違規。

傳遞*大小*大於*緩衝區*實際大小的值會導致緩衝區溢位。

## <a name="remarks"></a>備註

這些函式提供更安全的 **_strdate**和 **_wstrdate**版本。 **_Strdate_s**函式會將目前的系統日期複製到*緩衝區*所指向的緩衝區。 其格式`mm/dd/yy`為，其中`mm`是兩位數的月份， `dd`是兩位數的日，而`yy`是年份的最後兩個數字。 例如，字串 `12/05/99` 代表 1999 年 12 月 5 日。 緩衝區長度至少必須為9個字元。

**_wstrdate_s**是寬字元版本的 **_strdate_s**;**_wstrdate_s**的引數和傳回值是寬字元字串。 除此之外，這些函式的行為相同。

當*buffer*是**Null**指標，或*大小*少於9個字元時，就會叫用不正確參數處理常式。 它會在[參數驗證](../../c-runtime-library/parameter-validation.md)中說明。 如果允許繼續執行，這些函式會傳回-1。 如果緩衝區為**Null**或*大小*小於或等於0，則會將**errno**設定為**EINVAL** 。 或者，如果*大小*小於9，則會將**Errno**設定為**ERANGE** 。

在 c + + 中，樣板多載簡化了這些函式的使用方式。 多載可以自動推斷緩衝區長度，這樣就不需要指定*大小*引數。 而且，它們可以自動將不安全的函式取代為其較新且更安全的對應專案。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

這些函式的 debug 程式庫版本會先以0xFE 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應：

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
[asctime_s，_wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)\
[時間、_time32、_time64](time-time32-time64.md)\
[_tzset](tzset.md)
