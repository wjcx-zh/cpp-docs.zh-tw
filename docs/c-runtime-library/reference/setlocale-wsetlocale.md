---
title: setlocale、_wsetlocale
ms.date: 11/04/2016
apiname:
- _wsetlocale
- setlocale
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
ms.openlocfilehash: 618b3e58a52e89561439fe76bf1b30e3cbbce001
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356351"
---
# <a name="setlocale-wsetlocale"></a>setlocale、_wsetlocale

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

*category*<br/>
地區設定所影響的分類。

*locale*<br/>
地區設定指定名稱。

## <a name="return-value"></a>傳回值

如果有效*地區設定*並*類別目錄*所指定，讓指標回到指定相關聯的字串*地區設定*和*類別*。 如果*地區設定*或是*分類*無效，會傳回 null 指標，該程式的目前地區設定不會變更。

例如，呼叫

```C
setlocale( LC_ALL, "en-US" );
```

會設定所有分類，只傳回字串

```Output
en-US
```

您可以複製所傳回的字串**setlocale**還原該程式的地區設定資訊的部分。 全域或執行緒的本機儲存體使用於所傳回的字串**setlocale**。 稍後呼叫**setlocale**覆寫的字串，由先前呼叫所傳回的字串指標失效。

## <a name="remarks"></a>備註

使用**setlocale**來設定、 變更或查詢部分或所有目前程式地區設定資訊所指定的函式*地區設定*並*分類*。 *地區設定*指的是，您可以自訂某些方面，您的程式位置 （國家/地區和語言）。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。 如果您設定*地區設定*有支援您的電腦上的多種形式語言的預設字串，您應該檢查**setlocale**傳回值以查看哪種語言是作用中。 例如，如果您設定*地區設定*"中文 」 傳回的值可能是 「 中文簡體 」 或 「 繁體中文 」。

**_wsetlocale**是寬字元版本的**setlocale**;*地區設定*引數和傳回值 **_wsetlocale**是寬字元字串。 **_wsetlocale**並**setlocale**行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

*分類*引數會指定程式的地區設定資訊會受到影響的組件。 所使用的巨集*分類*和影響的程式部分如下所示：

|*類別目錄*旗標|Affects|
|-|-|
| **LC_ALL** | 所有分類，如下所示。 |
| **LC_COLLATE** | **Strcoll**， **_stricoll**， **wcscoll**， **_wcsicoll**， **strxfrm**， **_strncoll**， **_strnicoll**， **_wcsncoll**， **_wcsnicoll**，並**wcsxfrm**函式。 |
| **LC_CTYPE** | 字元處理函式 (除了**isdigit**， **isxdigit**， **mbstowcs**，以及**mbtowc**，這不會受到影響)。 |
| **LC_MONETARY** | 所傳回的貨幣格式資訊**localeconv**函式。 |
| **LC_NUMERIC** | 小數點字元的格式化的輸出常式 (例如**printf**)、 資料轉換常式，以及所傳回的非貨幣格式化資訊**localeconv**。 除了小數點字元以外**LC_NUMERIC**集千分位分隔符號和群組控制傳回字串[localeconv](localeconv.md)。 |
| **LC_TIME** | **Strftime**並**wcsftime**函式。 |

此函式會驗證分類參數。 如果分類參數不是前表中所指定的其中一個值，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會設定**errno**要**EINVAL** ，並傳回**NULL**。

*地區設定*引數是指定的地區設定字串的指標。 如需有關格式的資訊*地區設定*引數，請參閱[地區設定名稱、 語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 如果 *locale* 指向空字串，地區設定即為由實作所定義的原生環境。 值為**C**指定最小 ANSI 符合 C 轉譯環境。 **C**地區設定會假設所有**char**資料型別有 1 個位元組，且其值一律是小於 256。

在程式啟動時，將執行與下列陳述式相同的動作：

`setlocale( LC_ALL, "C" );`

*地區設定*引數可採用的地區設定名稱、 語言字串、 語言字串和國家/地區碼、 字碼頁，或語言字串、 國家/地區碼和字碼頁。 可用的地區設定名稱、語言、國家/地區碼和字碼頁的集合，包含所有 Windows NLS 應用程式開發介面 (API) 支援的所有項目，但不包含每個字元需要超過兩個位元組 (例如 UTF-7 及 UTF-8) 的字碼頁。 如果您提供 utf-7 或 utf-8 的字碼頁值**setlocale**將會失敗，傳回**NULL**。 一組支援的地區設定名稱**setlocale**所述[地區設定名稱、 語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 一組支援的語言和國家/地區字串**setlocale**所述[語言字串](../../c-runtime-library/language-strings.md)並[國家/地區字串](../../c-runtime-library/country-region-strings.md)。 我們建議使用內嵌於程式碼或針對儲存體序列化之地區設定字串的效能與維護所適用的地區設定名稱格式。 地區設定名稱字串比語言和國家/地區名稱格式更不容易被作業系統更新變更。

傳遞做為 null 指標*地區設定*引數會指示**setlocale**查詢而非設定國際環境。 如果*地區設定*引數為 null 指標，該程式的目前地區設定不會變更。 相反地， **setlocale**相關聯的字串中傳回的指標*分類*執行緒的目前地區設定。 如果*分類*引數是**LC_ALL**，函式會傳回字串，表示每個類別，以分號隔開的目前設定。 例如，呼叫的順序

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

這是相關聯的字串**LC_ALL**類別目錄。

下列範例與相關**LC_ALL**類別目錄。 字串「.OCP」或「.ACP」可以用來以分別指定使用者預設 OEM 字碼頁以及使用者預設 ANSI 字碼頁的用途，字碼頁編號則無法這麼做。

- `setlocale( LC_ALL, "" );`

   將地區設定設定為從作業系統取得的使用者預設 ANSI 字碼頁的預設值。

- `setlocale( LC_ALL, ".OCP" );`

   將地區設定明確設定為從作業系統取得的目前 OEM 字碼頁。

- `setlocale( LC_ALL, ".ACP" );`

   將地區設定設定為從作業系統取得的 ANSI 字碼頁。

- `setlocale( LC_ALL, "<localename>" );`

   將地區設定設為 \<地區設定名稱> 所表示的地區設定名稱。

- `setlocale( LC_ALL, "<language>_<country>" );`

   將地區設定設定為 \<語言> 和 \<國家/地區> 所表示的語言和國家/地區，以及從主機作業系統取得的預設字碼頁。

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   設定所指定的地區設定的語言、 國家/地區和字碼頁 *\<語言 >*， *\<國家/地區 >*，以及 *\<字碼頁>* 字串。 您可以使用各種語言、國家/地區和字碼頁的組合。 例如，此呼叫會以字碼頁 1252 將地區設定設為加拿大法文：

   `setlocale( LC_ALL, "French_Canada.1252" );`

   此呼叫會以預設 ANSI 字碼頁將地區設定設為加拿大法文：

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   此呼叫會以預設 OEM 字碼頁將地區設定設為加拿大法文：

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   將地區設定設定為\<語言>  所表示的語言，並使用指定語言的預設國家/地區，以及從主機作業系統取得之該國家/地區的使用者預設 ANSI 字碼頁。 例如，下列呼叫來**setlocale**相同的功能：

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   我們建議用於效能和維護的第一個格式。

- `setlocale( LC_ALL, ".<code_page>" );`

   將字碼頁設定為 <字碼頁> 所表示的值，以及指定字碼頁的預設國家/地區和語言 (由主機作業系統所定義)。

類別必須是**LC_ALL**或是**LC_CTYPE**以促使字碼頁中的變更。 例如，如果預設國家/地區和語言的主機作業系統是 「 美國 」 和 「 英文 」 下, 面兩個呼叫**setlocale**相同的功能：

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

如需詳細資訊，請參閱 [C/C++ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)中的 [setlocale](../../preprocessor/setlocale.md) pragma 指示詞。

此函式[_configthreadlocale](configthreadlocale.md)是用來控制**setlocale**會影響在程式中的所有執行緒的地區設定或只呼叫執行緒的地區設定。

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

[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale、_wcreate_locale](create-locale-wcreate-locale.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
