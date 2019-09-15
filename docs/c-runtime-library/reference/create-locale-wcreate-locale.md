---
title: _create_locale、_wcreate_locale
ms.date: 11/04/2016
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: a7098dc572ecdbefd891efc8443e977b01850fa4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938846"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale、_wcreate_locale

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

如果指定有效的*地區*設定和*分類*，則會傳回指定的地區設定做為 **_locale_t**物件。 但不會變更程式的目前地區設定。

## <a name="remarks"></a>備註

**_Create_locale**函式可讓您建立代表特定地區特定設定的物件，以用於許多 CRT 函式的地區設定特定版本（具有 **_l**尾碼的函數）。 此行為類似于**setlocale**，不同之處在于，不會將指定的地區設定套用至目前的環境，而是將設定儲存在傳回的 **_locale_t**結構中。 當不再需要 **_locale_t**結構時，應該使用[_free_locale](free-locale.md)加以釋放。

**_wcreate_locale**是寬字元版本的 **_create_locale**; **_wcreate_locale**的*地區*設定引數是寬字元字串。 相反地， **_wcreate_locale**和 **_create_locale**的行為相同。

*Category*引數會指定受影響之地區設定特定行為的部分。 用於*分類*的旗標及其影響的程式部分如下表所示：

| *類別*旗標 | Affects |
|-----------------|---------|
| **LC_ALL** |所有分類，如下所示。 |
| **LC_COLLATE** |**Strcoll**、 **_stricoll**、 **wcscoll**、 **_wcsicoll**、 **strxfrm**、 **_strncoll**、 **_strnicoll**、 **_wcsncoll**、 **_wcsnicoll**和**wcsxfrm**函數。 |
| **LC_CTYPE** | 字元處理函式（不受影響的**isdigit**、 **isxdigit**、 **mbstowcs**和**mbtowc**除外）。 |
| **LC_MONETARY** | **Localeconv**函數所傳回的貨幣格式資訊。 |
| **LC_NUMERIC** | 格式化輸出常式（例如**printf**）的小數點字元、資料轉換常式，以及**localeconv**所傳回的非貨幣格式資訊。 除了小數點字元以外， **LC_NUMERIC**會設定[localeconv](localeconv.md)所傳回的千位分隔符號和群組控制字元串。 |
| **LC_TIME** | **Strftime**和**wcsftime**函數。 |

此函式會驗證*分類*和*地區*設定參數。 如果 category 參數不是上表中所指定的其中一個值，或*地區*設定為**null**，則函式會傳回**null**。

*Locale*引數是指定地區設定之字串的指標。 如需*地區*設定引數格式的詳細資訊，請參閱[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。

*地區*設定引數可以採用地區設定名稱、語言字串、語言字串和國家/地區代碼、字碼頁，或語言字串、國家/地區碼和字碼頁。 可用的地區設定名稱、語言、國家/區域碼和字碼頁的集合，包含 Windows NLS API 支援的所有項目，但不包含每個字元需要超過兩個位元組 (例如 UTF-7 及 UTF-8) 的字碼頁。 如果您提供像是 UTF-7 或 UTF-8 的字碼頁， **_create_locale**將會失敗，並傳回**Null**。 地區設定[名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中會描述 **_create_locale**所支援的地區設定名稱集合。 **_Create_locale**支援的一組語言和國家/地區字串會列在[語言字串](../../c-runtime-library/language-strings.md)和[國家/地區字串](../../c-runtime-library/country-region-strings.md)中。

如需地區設定的詳細資訊，請參閱 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。

這個函式的先前名稱 **__create_locale** （有兩個前置底線）已被取代。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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

[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
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
