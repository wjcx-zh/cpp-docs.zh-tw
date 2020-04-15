---
title: _create_locale、_wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 611eaf342776b9a0f57c4f55c52a841c3fd13fb5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348259"
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

*類別*<br/>
分類。

*現場*<br/>
地區設定指定名稱。

## <a name="return-value"></a>傳回值

如果提供了有效的*區域設置*和*類別*,則返回指定的區域設置作為 **_locale_t**物件。 但不會變更程式的目前地區設定。

## <a name="remarks"></a>備註

**_create_locale**函數允許您創建表示特定區域設置的物件,以便在許多 CRT 函數的區域設置特定版本中使用(具有 **_l**後綴的函數)。 該行為類似於**setlocale,** 只不過,這些設置不是將指定的區域設置應用於當前環境,而是保存在返回 **_locale_t**結構中。 當不再需要 **_locale_t**結構時,應使用[_free_locale](free-locale.md)釋放結構。

**_wcreate_locale**是 **_create_locale**的寬字元版本;從 **_wcreate_locale***區域設定*參數是寬字元字串。 **_wcreate_locale**和 **_create_locale**行為相同。

*類別*參數指定受影響的特定於區域設置的行為的部分。 類別*的*標誌及其影響的程式部分如下表所示:

| *類別*標誌 | 影響 |
|-----------------|---------|
| **LC_ALL** |所有分類，如下所示。 |
| **LC_COLLATE** |**斯特科爾****,_stricoll,wcscoll,_wcsicoll,****斯特克斯弗姆****_stricoll****_wcsicoll**,_strncoll,_strnicoll,_wcsncoll,_wcsnicoll,和**wcsxfrm**功能。 **_strncoll** **_strnicoll** **_wcsncoll** **_wcsnicoll** |
| **LC_CTYPE** | 字元處理函數(除**數位****、isxdigit、mbstowcs**和**mbtowc** **mbstowcs** (未受影響) |
| **LC_MONETARY** | **本地 econv**函數傳回的貨幣格式資訊。 |
| **LC_NUMERIC** | 格式化的輸出例程(如**printf**)的數據轉換例程和**localeconv**傳回的非貨幣格式資訊的十進位元字元。 除了小數點字元外 **,LC_NUMERIC**設置數千分隔元和[由 localeconv](localeconv.md)返回的分組控制字串。 |
| **LC_TIME** | **穩時**和**wcsftime**函數。 |

此函數驗證*類別*和*區域設置*參數。 如果類別參數不是上表中給出的值之一,或者如果*區域設定*為**NULL,** 則函數將傳回**NULL**。

*區域設定*參數是指向指定區域設置的字串的指標。 關於*區域設定*參數格式的資訊,請參閱[區域設定名稱、語言和國家/ 區域字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。

*區域設置*參數可以採用區域設置名稱、語言字串、語言字串和國家/地區代碼、代碼頁或語言字串、國家/區域代碼和代碼頁。 可用的區域設定名稱、語言、國家/地區代碼和代碼頁集包括 Windows NLS API 支援的所有區域設定名稱、 語言/區域代碼和代碼頁。 **_create_locale**支援的區域設置名稱集在[區域設置名稱、語言和國家/區域字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中描述。 **_create_locale**支援的語言和國家/區域字串集列在[語言字串](../../c-runtime-library/language-strings.md)和國家[/區域字串](../../c-runtime-library/country-region-strings.md)中。

如需地區設定的詳細資訊，請參閱 [setlocale、_wsetlocale](setlocale-wsetlocale.md)。

此函數的前一個名稱 **__create_locale(** 具有兩個前導下劃線)已被棄用。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

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

[區域設定名稱、語言和國家/區域字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[語言字串](../../c-runtime-library/language-strings.md)<br/>
[國家/地區字串](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[設定區域設定](../../preprocessor/setlocale.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
