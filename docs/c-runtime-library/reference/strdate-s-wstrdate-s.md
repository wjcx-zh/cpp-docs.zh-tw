---
title: _strdate_s、_wstrdate_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strdate_s
- _wstrdate_s
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
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4e9ff3783fc7a89e7af42ebf283209c034c0d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414307"
---
# <a name="strdates-wstrdates"></a>_strdate_s、_wstrdate_s

將目前的系統日期複製到緩衝區。 這些是 [_strdate、_wstrdate](strdate-wstrdate.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _strdate_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t numberOfElements
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

*buffer*<br/>
將填入格式化日期字串之緩衝區的指標。

*numberOfElements*<br/>
緩衝區的大小。

## <a name="return-value"></a>傳回值

如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼在 EERRNO.H 中定義，請參閱下表查看此函式產生的確切錯誤。 如需錯誤碼的詳細資訊，請參閱 [errno](../../c-runtime-library/errno-constants.md)。

## <a name="error-conditions"></a>錯誤狀況

|*buffer*|*numberOfElements*|Return|內容*緩衝區*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(任何)|**EINVAL**|未修改|
|不**NULL** （指向有效的緩衝區）|0|**EINVAL**|未修改|
|不**NULL** （指向有效的緩衝區）|0 < *numberOfElements* < 9|**EINVAL**|空字串|
|不**NULL** （指向有效的緩衝區）|*numberOfElements* > = 9|0|目前的日期格式一如＜備註＞所指定|

## <a name="security-issues"></a>安全性問題

傳遞無效的非**NULL**當緩衝區就會發生存取違規的值*numberOfElements*參數大於 9。

傳遞大小的值大於實際大小*緩衝區*會導致緩衝區滿溢。

## <a name="remarks"></a>備註

這些函式提供更安全的版本 **_strdate**和 **_wstrdate**。 **_Strdate_s**函式會複製到所指向之緩衝區的目前系統日期*緩衝區*格式化**公釐**/**dd** / **yy**，其中**公釐**是兩位數表示月份， **dd**是兩位數代表日期，以及**yy**是兩位數的年份。 例如，字串**12/05/99**代表 1999 年 12 月 5 日。 緩衝區長度至少必須是 9 個字元。

**_wstrdate_s**是寬字元版本的 **_strdate_s**; 的引數和傳回值 **_wstrdate_s**是寬字元字串。 除此之外，這些函式的行為相同。

如果*緩衝區*是**NULL**指標，或如果*numberOfElements*小於 9 個字元、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回-1，並設定**errno**至**EINVAL**如果緩衝區已**NULL**或*numberOfElements*小於或等於 0 或一組**errno**至**為 ERANGE**如果*numberOfElements*少於 9。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mapping"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> 或 \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>範例

請參閱 [time](time-time32-time64.md) 的範例。

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
