---
title: setlocale, _wsetlocale
description: 描述 Microsoft C 執行時setlocale_wsetlocale(CRT) 函式庫函數與 。
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
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
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 2834229839153c3154caadf71e5fb30d84ed2f1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353715"
---
# <a name="setlocale-_wsetlocale"></a>setlocale、_wsetlocale

設定或擷取執行階段地區設定。

## <a name="syntax"></a>語法

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>參數

*類別*\
地區設定所影響的分類。

*現場*\
地區設定指定名稱。

## <a name="return-value"></a>傳回值

如果提供了有效的*區域設置*和*類別*,則傳回指向與指定*區域設置*和*類別*關聯的字串的指標。 如果*區域設置*或*類別*無效,請返回一個空指標,並且程式的當前區域設置保持不變。

例如，呼叫

```C
setlocale( LC_ALL, "en-US" );
```

會設定所有分類，只傳回字串

```Output
en-US
```

您可以複製透過**setlocale**傳回的字串,以還原程式區域設定資訊的該部分。 全域或線程本地儲存用於**由 setlocale**傳回的字串。 稍後呼叫**設定本地設定**覆蓋字串,該字串使早期呼叫返回的字串指標無效。

## <a name="remarks"></a>備註

使用**setlocale**函數設定、更改或查詢*區域設置*和*類別*指定的部分或全部當前程式區域設置資訊。 *區域設置*是指您可以自定義程式某些方面的地方(國家/地區和語言)。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。 如果將*區域設置*設置為計算機上支援多個窗體的語言的預設字串,則應檢查**設置區域設置**返回值以查看哪種語言有效。 例如,如果將*區域設置*設置為「中文」,則返回值可以是「中文簡化」或「中文-傳統」。

**_wsetlocale**是**集本地的**寬字元版本;**_wsetlocale**的*區域設定*參數和返回值是寬字元字串。 **_wsetlocale**和**設置局部性**行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**設定區域設定**|**設定區域設定**|**_wsetlocale**|

*類別*參數指定程式區域設置資訊受影響的部分。 用於*類別*的宏及其影響的程式部分如下所示:

|*類別*標誌|影響|
|-|-|
| **LC_ALL** | 所有分類，如下所示。 |
| **LC_COLLATE** | **斯特科爾****,_stricoll,wcscoll,_wcsicoll,****斯特克斯弗姆****_stricoll****_wcsicoll**,_strncoll,_strnicoll,_wcsncoll,_wcsnicoll,和**wcsxfrm**功能。 **_strncoll** **_strnicoll** **_wcsncoll** **_wcsnicoll** |
| **LC_CTYPE** | 字元處理函數(除**數位****、isxdigit、mbstowcs**和**mbtowc** **mbstowcs** (未受影響) |
| **LC_MONETARY** | **本地 econv**函數傳回的貨幣格式資訊。 |
| **LC_NUMERIC** | 格式化的輸出例程(如**printf**)的數據轉換例程和**localeconv**傳回的非貨幣格式資訊的十進位元字元。 除了小數點字元外 **,LC_NUMERIC**設置數千分隔元和[由 localeconv](localeconv.md)返回的分組控制字串。 |
| **LC_TIME** | **穩時**和**wcsftime**函數。 |

此函式會驗證分類參數。 如果類別參數不是上表中給出的值之一,則調用無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將**errno**設定到**EINVAL**並傳回**NULL**。

*區域設定*參數是指向指定區域設置的字串的指標。 關於*區域設定*參數格式的資訊,請參閱[區域設定名稱、語言和國家/ 區域字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 如果 *locale* 指向空字串，地區設定即為由實作所定義的原生環境。 **值 C**指定 C 轉換的最小 ANSI 符合環境。 **C**區域設置假定所有**字元**數據類型為1位元組,其值始終小於256。

在程式啟動時，將執行與下列陳述式相同的動作：

`setlocale( LC_ALL, "C" );`

*區域設置*參數可以採用區域設置名稱、語言字串、語言字串和國家/地區代碼、代碼頁或語言字串、國家/區域代碼和代碼頁。 可用的區域設定名稱、語言、國家/地區代碼和代碼頁集包括 Windows NLS API 支援的所有區域設置名稱、語言/區域代碼和代碼頁。 **setlocale**支援的區域設置名稱集在[區域設置名稱、語言和國家/區域字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中描述。 **設定區域設置**支援的語言和國家/區域字串集列在[語言字串](../../c-runtime-library/language-strings.md)和國家[/區域字串](../../c-runtime-library/country-region-strings.md)中。 我們建議使用內嵌於程式碼或針對儲存體序列化之地區設定字串的效能與維護所適用的地區設定名稱格式。 地區設定名稱字串比語言和國家/地區名稱格式更不容易被作業系統更新變更。

作為*區域設置*參數傳遞的空指標告訴**setlocale**進行查詢,而不是設置國際環境。 如果*區域設置*參數為空指標,則程式的當前區域設置不會更改。 相反,**設定區域設置**傳回指向與線程當前區域設置*的類別*關聯的字串的指標。 如果*類別*參數**為LC_ALL,** 則函數將返回一個字串,該字串指示每個類別的當前設置,以分號分隔。 例如，呼叫的順序

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

傳回

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

是與**LC_ALL**類別關聯的字串。

以下示例與**LC_ALL**類別有關。 任一字串"OCP"和"。可以使用 ACP"而不是代碼頁碼來分別指定使用使用者預設 OEM 代碼頁和使用者預設 ANSI 代碼頁。這些代碼頁是該區域設置名稱的。

- `setlocale( LC_ALL, "" );`

   將地區設定設定為從作業系統取得的使用者預設 ANSI 字碼頁的預設值。 區域設置名稱設置為[GetUserDefaultlocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)傳回的值。 代碼頁設置為[GetACP](/windows/win32/api/winnls/nf-winnls-getacp)返回的值。

- `setlocale( LC_ALL, ".OCP" );`

   將區域設置設置到從作業系統獲取的目前 OEM 代碼頁。 區域設置名稱設置為[GetUserDefaultlocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)傳回的值。 代碼頁由[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)設置為使用者預設區域設置名稱[LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, ".ACP" );`

   將地區設定設定為從作業系統取得的 ANSI 字碼頁。 區域設置名稱設置為[GetUserDefaultlocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename)傳回的值。 代碼頁由[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)設置為使用者預設區域設置名稱[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, "<localename>" );`

   將區域設置設置到區域設置名稱(由*\<區域名稱>* 指示區域設置名稱。 代碼頁由[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)設定為指定區域設置名稱[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, "<language>_<country>" );`

   將區域設置設置為*\<語言>* 和國家*\</地區>* 所指示的語言和國家/地區,以及從主機操作系統獲取的默認代碼頁。 代碼頁由[GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex)設定為指定區域設置名稱[LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants)值。

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   將區域設置設置為*\<語言*、國家/地區和代碼頁,由語言>、*\<國家>* 和*\<code_page>* 字串元指示。 您可以使用各種語言、國家/地區和字碼頁的組合。 例如，此呼叫會以字碼頁 1252 將地區設定設為加拿大法文：

   `setlocale( LC_ALL, "French_Canada.1252" );`

   此呼叫會以預設 ANSI 字碼頁將地區設定設為加拿大法文：

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   此呼叫會以預設 OEM 字碼頁將地區設定設為加拿大法文：

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   將區域設置設定為*\<語言>* 的語言,並使用指定語言的預設國家/區域以及從主機操作系統獲取的該國家/地區的使用者預設 ANSI 代碼頁。 例如,以下用於**設定本地的**呼叫在功能上等效:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   我們建議用於效能和維護的第一個格式。

- `setlocale( LC_ALL, ".<code_page>" );`

   將字碼頁設定為 <字碼頁>** 所表示的值，以及指定字碼頁的預設國家/地區和語言 (由主機作業系統所定義)。

類別必須**LC_ALL**或**LC_CTYPE**才能對代碼頁進行更改。 例如,如果主機作業系統的預設國家/區域和語言是「美國」和「英語」,則以下兩個設置**本地狀態**的調用在功能上等效:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

如需詳細資訊，請參閱 [C/C++ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)中的 [setlocale](../../preprocessor/setlocale.md) pragma 指示詞。

函數[_configthreadlocale](configthreadlocale.md)用於控制**設置區域設置**是影響程式中所有線程的區域設置,還是僅影響調用線程區域設置。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
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
           setlocale(LC_ALL, locale));

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
           setlocale(LC_ALL, "en-US"));

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

[區域設定名稱、語言和國家/區域字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale,_wcreate_locale](create-locale-wcreate-locale.md)\
[現場](../../c-runtime-library/locale.md)\
[當地科恩夫](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[斯特倫, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[_mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[_mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[斯特科爾功能](../../c-runtime-library/strcoll-functions.md)\
[時間,wcsftime,_strftime_l,_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[斯特克斯弗姆, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[_wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb、_wctomb_l](wctomb-wctomb-l.md)
