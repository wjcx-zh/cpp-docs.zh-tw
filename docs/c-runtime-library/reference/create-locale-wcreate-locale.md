---
title: _create_locale、_wcreate_locale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- create_locale
- _create_locale
- __create_locale
dev_langs:
- C++
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9be41a2d156a522c74349c3457295502ae6d4f43
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451936"
---
# <a name="createlocale-wcreatelocale"></a>_create_locale、_wcreate_locale

建立地區設定物件。

## <a name="syntax"></a>語法

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>參數

*category*<br/>
分類。

*locale*<br/>
地區設定指定名稱。

## <a name="return-value"></a>傳回值

如果是有效*地區設定*和*類別*指定，會傳回指定的地區設定設定為 **_locale_t**物件。 但不會變更程式的目前地區設定。

## <a name="remarks"></a>備註

**_Create_locale**函式可讓您建立物件，代表特定的特定地區設定，以用於地區設定特定版本的許多 CRT 函式 (函式與 **_l**尾碼). 作法就類似於**setlocale**，不過，而不是指定的地區設定設定套用到目前的環境，這些設定會儲存在 **_locale_t**傳回的結構。 **_Locale_t**結構應該使用釋放[_free_locale](free-locale.md)不再需要時。

**_wcreate_locale**是寬字元版本的 **_create_locale**;*地區設定*引數 **_wcreate_locale**是寬字元字串。 **_wcreate_locale**和 **_create_locale**除此之外的行為相同。

*類別*引數會指定地區設定特定行為受影響的部分。 使用的旗標*類別*，它們會影響的程式的部分是下表所示。

|*類別*旗標|Affects|
|-|-|
**LC_ALL**|所有分類，如下所示。
**LC_COLLATE**|**Strcoll**， **_stricoll**， **wcscoll**， **_wcsicoll**， **strxfrm**， **_strncoll**， **_strnicoll**， **_wcsncoll**， **_wcsnicoll**，和**wcsxfrm**函式。
**LC_CTYPE**|字元處理函式 (除了**isdigit**， **isxdigit**， **mbstowcs**，和**mbtowc**，這不受影響)。
**LC_MONETARY**|所傳回的貨幣格式資訊**localeconv**函式。
**LC_NUMERIC**|小數點字元適用於格式化的輸出常式 (例如**printf**)、 資料轉換常式和非貨幣格式化資訊傳回**localeconv**。 除了小數點字元**LC_NUMERIC**集千分位分隔符號和群組控制項所傳回的字串[localeconv](localeconv.md)。
**LC_TIME**|**Strftime**和**wcsftime**函式。

此函式會驗證*類別*和*地區設定*參數。 如果分類參數不是其中一個前述表格中所指定的值或*地區設定*是**NULL**，此函數會傳回**NULL**。

*地區設定*引數是指定的地區設定字串的指標。 如需有關的格式資訊*地區設定*引數，請參閱[地區設定名稱、 語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。

*地區設定*引數可以讀取地區設定名稱、 語言字串、 語言字串和國家/地區碼、 字碼頁或語言字串、 國家/地區碼和字碼頁。 可用的地區設定名稱、語言、國家/區域碼和字碼頁的集合，包含 Windows NLS API 支援的所有項目，但不包含每個字元需要超過兩個位元組 (例如 UTF-7 及 UTF-8) 的字碼頁。 如果您提供 utf-7 或 utf-8 的字碼頁 **_create_locale**失敗，並傳回**NULL**。 支援的地區設定名稱設定 **_create_locale**詳述於[地區設定名稱、 語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 支援的語言和國家/地區字串組 **_create_locale**會列在[語言字串](../../c-runtime-library/language-strings.md)和[國家/地區字串](../../c-runtime-library/country-region-strings.md)。

如需地區設定的詳細資訊，請參閱 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。

舊名稱的這個函式， **__create_locale** （具有兩個的前置底線），已被取代。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>另請參閱

[地區設定名稱、 語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[語言字串](../../c-runtime-library/language-strings.md)<br/>
[國家/地區字串](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
