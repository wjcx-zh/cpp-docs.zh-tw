---
title: ':::no-loc(setlocale):::, :::no-loc(_wsetlocale):::'
description: '描述 Microsoft C runtime （CRT）程式庫函數 :::no-loc(setlocale)::: 和 :::no-loc(_wsetlocale)::: 。'
ms.date: 4/2/2020
api_name:
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(setlocale):::'
- '_o_:::no-loc(_wsetlocale):::'
- '_o_:::no-loc(setlocale):::'
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ':::no-loc(_wsetlocale):::'
- '_t:::no-loc(setlocale):::'
- ':::no-loc(setlocale):::'
helpviewer_keywords:
- 'w:::no-loc(setlocale)::: function'
- ':::no-loc(setlocale)::: function'
- 't:::no-loc(setlocale)::: function'
- locales, defining
- '_t:::no-loc(setlocale)::: function'
- defining locales
- ':::no-loc(_wsetlocale)::: function'
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
no-loc:
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
ms.openlocfilehash: 05e4e96297e2237ed6768e05ff4cacfd63744e1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226134"
---
# <a name="no-locsetlocale-no-loc_wsetlocale"></a>:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::

設定或擷取執行階段地區設定。

## <a name="syntax"></a>語法

```C
char *:::no-loc(setlocale):::(
   int category,
   const char *locale
);
wchar_t *:::no-loc(_wsetlocale):::(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>參數

*category*\
地區設定所影響的分類。

*語言*\
地區設定指定名稱。

## <a name="return-value"></a>傳回值

如果指定有效的*地區*設定和*分類*，則會傳回與指定的*地區*設定和*分類*相關聯之字串的指標。 如果*地區*設定或*類別*無效，則會傳回 null 指標，而程式目前的地區設定則不會變更。

例如，呼叫

```C
:::no-loc(setlocale):::( LC_ALL, "en-US" );
```

會設定所有分類，只傳回字串

```Output
en-US
```

您可以複製所傳回的字串， **:::no-loc(setlocale):::** 以還原程式地區設定資訊的該部分。 全域或執行緒區域儲存區會用於所傳回的字串 **:::no-loc(setlocale):::** 。 稍後會呼叫來 **:::no-loc(setlocale):::** 覆寫字串，這會使先前呼叫所傳回的字串指標失效。

## <a name="remarks"></a>備註

您 **:::no-loc(setlocale):::** 可以使用函數來設定、變更或查詢*locale*和*category*所指定的部分或所有目前程式地區設定資訊。 *地區*設定是指您可以自訂程式某些層面的位置（國家/地區和語言）。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。 如果您將*地區*設定設為在電腦上支援多個表單之語言的預設字串，則應檢查傳回 **:::no-loc(setlocale):::** 值，以查看有哪些語言正在作用中。 例如，如果您將*地區*設定設為 "中文"，則傳回值可以是「簡體中文」或「繁體中文」。

**:::no-loc(_wsetlocale):::** 是的寬字元版本 **:::no-loc(setlocale):::** ; 的*地區*設定引數和傳回值 **:::no-loc(_wsetlocale):::** 是寬字元字串。 **:::no-loc(_wsetlocale):::** 和的 **:::no-loc(setlocale):::** 行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_t:::no-loc(setlocale):::**|**:::no-loc(setlocale):::**|**:::no-loc(setlocale):::**|**:::no-loc(_wsetlocale):::**|

*Category*引數會指定程式的地區設定資訊中受影響的部分。 用於*分類*的宏和其影響的程式部分如下所示：

|*類別*旗標|影響|
|-|-|
| **LC_ALL** | 所有分類，如下所示。 |
| **LC_COLLATE** | **Strcoll**、 **_stricoll**、 **wcscoll**、 **_wcsicoll**、 **strxfrm**、 **_strncoll**、 **_strnicoll**、 **_wcsncoll**、 **_wcsnicoll**和**wcsxfrm**函數。 |
| **LC_CTYPE** | 字元處理函式（不受影響的**isdigit**、 **isxdigit**、 **mbstowcs**和**mbtowc**除外）。 |
| **LC_MONETARY** | **Localeconv**函數所傳回的貨幣格式資訊。 |
| **LC_NUMERIC** | 格式化輸出常式（例如**printf**）的小數點字元、資料轉換常式，以及**localeconv**所傳回的非貨幣格式資訊。 除了小數點字元以外， **LC_NUMERIC**會設定[localeconv](localeconv.md)所傳回的千位分隔符號和群組控制字元串。 |
| **LC_TIME** | **Strftime**和**wcsftime**函數。 |

此函式會驗證分類參數。 如果 category 參數不是上表中指定的其中一個值，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會將**errno**設定為**EINVAL** ，並傳回**Null**。

*Locale*引數是指定地區設定之字串的指標。 如需*地區*設定引數格式的詳細資訊，請參閱[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 如果 *locale* 指向空字串，地區設定即為由實作所定義的原生環境。 **C**的值指定 c 轉譯的最低 ANSI 符合標準環境。 **C**地區設定會假設所有 **`char`** 資料類型都是1位元組，而且其值一律小於256。

在程式啟動時，將執行與下列陳述式相同的動作：

`:::no-loc(setlocale):::( LC_ALL, "C" );`

*地區*設定引數可以採用地區設定名稱、語言字串、語言字串和國家/地區代碼、字碼頁，或語言字串、國家/地區碼和字碼頁。 可用的地區設定名稱、語言、國家/地區碼和字碼頁的集合包含 Windows NLS API 所支援的所有功能。 所支援的地區設定名稱集合 **:::no-loc(setlocale):::** 會在地區設定[名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中說明。 支援的語言和國家/地區字串集合 **:::no-loc(setlocale):::** 會列在[語言字串](../../c-runtime-library/language-strings.md)和[國家/地區字串](../../c-runtime-library/country-region-strings.md)中。 我們建議使用內嵌於程式碼或針對儲存體序列化之地區設定字串的效能與維護所適用的地區設定名稱格式。 地區設定名稱字串比語言和國家/地區名稱格式更不容易被作業系統更新變更。

當做*地區*設定引數傳遞的 null 指標會告訴 **:::no-loc(setlocale):::** 查詢，而不是設定國際環境。 如果*locale*引數為 null 指標，則不會變更程式目前的地區設定。 相反 **:::no-loc(setlocale):::** 地，會傳回與執行緒目前地區設定的*類別*相關聯之字串的指標。 如果*分類*引數是**LC_ALL**，此函式會傳回字串，指出每個分類的目前設定（以分號分隔）。 例如，呼叫的順序

```C
// Set all categories and return "en-US"
:::no-loc(setlocale):::(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
:::no-loc(setlocale):::(LC_MONETARY, "fr-FR");
printf("%s\n", :::no-loc(setlocale):::(LC_ALL, NULL));
```

傳回

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

這是與**LC_ALL**分類相關聯的字串。

下列範例與**LC_ALL**分類有關。 任一字串」。OCP "and"。您可以使用 ACP，而不是字碼頁編號，分別指定使用者預設的 OEM 字碼頁，以及該地區設定名稱的使用者預設 ANSI 字碼頁。

- `:::no-loc(setlocale):::( LC_ALL, "" );`

   將地區設定設定為從作業系統取得的使用者預設 ANSI 字碼頁的預設值。 地區設定名稱會設為[GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)所傳回的值。 字碼頁會設定為[GetACP](/windows/win32/api/winnls/nf-winnls-getacp)所傳回的值。

- `:::no-loc(setlocale):::( LC_ALL, ".OCP" );`

   將地區設定設為從作業系統取得的目前 OEM 字碼頁。 地區設定名稱會設為[GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)所傳回的值。 [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)會將字碼頁設定為使用者預設地區設定名稱的[LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `:::no-loc(setlocale):::( LC_ALL, ".ACP" );`

   將地區設定設定為從作業系統取得的 ANSI 字碼頁。 地區設定名稱會設為[GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)所傳回的值。 [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)會將字碼頁設定為使用者預設地區設定名稱的[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `:::no-loc(setlocale):::( LC_ALL, "<localename>" );`

   將地區設定設為所表示的地區設定名稱 *\<localename>* 。 針對指定的地區設定名稱，使用[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)，將字碼頁設為[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `:::no-loc(setlocale):::( LC_ALL, "<language>_<country>" );`

   將地區設定設為和所指示的語言和國家/地區 *\<language>* *\<country>* ，以及從主機作業系統取得的預設字碼頁。 針對指定的地區設定名稱，使用[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)，將字碼頁設為[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `:::no-loc(setlocale):::( LC_ALL, "<language>_<country>.<code_page>" );`

   將地區設定設為、和字串所表示的語言、國家/地區和字碼頁 *\<language>* *\<country>* *\<code_page>* 。 您可以使用各種語言、國家/地區和字碼頁的組合。 例如，此呼叫會以字碼頁 1252 將地區設定設為加拿大法文：

   `:::no-loc(setlocale):::( LC_ALL, "French_Canada.1252" );`

   此呼叫會以預設 ANSI 字碼頁將地區設定設為加拿大法文：

   `:::no-loc(setlocale):::( LC_ALL, "French_Canada.ACP" );`

   此呼叫會以預設 OEM 字碼頁將地區設定設為加拿大法文：

   `:::no-loc(setlocale):::( LC_ALL, "French_Canada.OCP" );`

- `:::no-loc(setlocale):::( LC_ALL, "<language>" );`

   將地區設定設為所表示的語言 *\<language>* ，並使用指定語言的預設國家/地區，以及從主機作業系統取得之該國家/地區的使用者預設 ANSI 字碼頁。 例如，下列對的呼叫 **:::no-loc(setlocale):::** 在功能上是相同的：

   `:::no-loc(setlocale):::( LC_ALL, "en-US" );`

   `:::no-loc(setlocale):::( LC_ALL, "English" );`

   `:::no-loc(setlocale):::( LC_ALL, "English_United States.1252" );`

   我們建議用於效能和維護的第一個格式。

- `:::no-loc(setlocale):::( LC_ALL, ".<code_page>" );`

   將字碼頁設定為 <字碼頁>** 所表示的值，以及指定字碼頁的預設國家/地區和語言 (由主機作業系統所定義)。

分類必須是**LC_ALL**或**LC_CTYPE** ，才會影響字碼頁的變更。 例如，如果主機作業系統的預設國家/地區和語言是「美國」和「英文」，則下列兩個呼叫在 **:::no-loc(setlocale):::** 功能上是相同的：

`:::no-loc(setlocale):::( LC_ALL, ".1252" );`

`:::no-loc(setlocale):::( LC_ALL, "English_United States.1252");`

如需詳細資訊，請參閱 [:::no-loc(setlocale):::](../../preprocessor/:::no-loc(setlocale):::.md) [C/c + + 預處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)中的 pragma 指示詞。

函式[_configthreadlocale](configthreadlocale.md)是用來控制是否 **:::no-loc(setlocale):::** 會影響程式中所有線程的地區設定，或是只有呼叫執行緒的地區設定。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**:::no-loc(setlocale):::**|\<locale.h>|
|**:::no-loc(_wsetlocale):::**|\<locale.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_:::no-loc(setlocale):::.c
//
// This program demonstrates the use of :::no-loc(setlocale)::: when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           :::no-loc(setlocale):::(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           :::no-loc(setlocale):::(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>另請參閱

[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale，_wcreate_locale](create-locale-wcreate-locale.md)\
[語言](../../c-runtime-library/locale.md)\
[localeconv](localeconv.md)\
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)\
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs，_mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc，_mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)\
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs，_wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb、_wctomb_l](wctomb-wctomb-l.md)
