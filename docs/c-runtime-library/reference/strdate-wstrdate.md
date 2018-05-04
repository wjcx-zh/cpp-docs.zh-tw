---
title: _strdate、_wstrdate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strdate
- _wstrdate
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
- _tstrdate
- wstrdate
- _wstrdate
- _strdate
- strdate
dev_langs:
- C++
helpviewer_keywords:
- strdate function
- dates, copying
- tstrdate function
- _wstrdate function
- wstrdate function
- _strdate function
- _tstrdate function
- copying dates
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8924ac1ad29408dd1d69a68c6f31d9194831fbc2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="strdate-wstrdate"></a>_strdate、_wstrdate

將目前的系統日期複製到緩衝區。 這些函式已有更安全的版本可用，請參閱 [_strdate_s、_wstrdate_s](strdate-s-wstrdate-s.md)。

## <a name="syntax"></a>語法

```C
char *_strdate(
   char *datestr
);
wchar_t *_wstrdate(
   wchar_t *datestr
);
template <size_t size>
char *_strdate(
   char (&datestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrdate(
   wchar_t (&datestr)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*datestr*<br/>
包含格式化日期字串之緩衝區的指標。

## <a name="return-value"></a>傳回值

所有這些函式會傳回產生的字元字串的指標*datestr*。

## <a name="remarks"></a>備註

這些函式已有更安全的版本可用，請參閱 [_strdate_s、_wstrdate_s](strdate-s-wstrdate-s.md)。 建議您盡可能使用更安全的函式。

**_Strdate**函式會複製到所指向之緩衝區的目前系統日期*datestr*格式化**公釐**/**dd** / **yy**，其中**公釐**是兩位數表示月份， **dd**是兩位數代表日期，以及**yy**是兩位數的年份。 例如，字串**12/05/99**代表 1999 年 12 月 5 日。 緩衝區長度至少必須是 9 個位元組。

如果*datestr*是**NULL**指標、 無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回-1，並設定**errno**至**EINVAL**。

**_wstrdate**是寬字元版本的 **_strdate**; 的引數和傳回值 **_wstrdate**是寬字元字串。 除此之外，這些函式的行為相同。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate**|**_strdate**|**_strdate**|**_wstrdate**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// strdate.c
// compile with: /W3
#include <time.h>
#include <stdio.h>
int main()
{
    char tmpbuf[9];

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996
    // Note: _strdate is deprecated; consider using _strdate_s instead
}
```

```Output
OS date: 04/25/03
```

## <a name="see-also"></a>另請參閱

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
