---
title: "setlocale、_wsetlocale | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0610dff5366f72010de965b7b9df0cd4e02c1e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setlocale-wsetlocale"></a>setlocale、_wsetlocale
設定或擷取執行階段地區設定。  
  
## <a name="syntax"></a>語法  
  
```  
char *setlocale(  
   int category,  
   const char *locale   
);  
wchar_t *_wsetlocale(  
   int category,  
   const wchar_t *locale   
);  
```  
  
#### <a name="parameters"></a>參數  
 `category`  
 地區設定所影響的分類。  
  
 `locale`  
 地區設定指定名稱。  
  
## <a name="return-value"></a>傳回值  
 如果指定有效的 `locale` 和 `category`，將會傳回指向與指定之 `locale` 和 `category` 相關聯字串的指標。 如果 `locale` 或 `category` 無效，則傳回 null 指標，不會變更程式目前的地區設定。  
  
 例如，呼叫  
  
 `setlocale( LC_ALL, "en-US" );`  
  
 會設定所有分類，只傳回字串  
  
 `en-US`  
  
 您可以複製 `setlocale` 所傳回的字串，還原程式的地區設定資訊部分。 全域或執行緒區域儲存區可用於 `setlocale` 所傳回的字串。 對 `setlocale` 的後續呼叫會覆寫字串，使先前呼叫所傳回的字串指標失效。  
  
## <a name="remarks"></a>備註  
 使用 `setlocale` 函式可設定、變更或查詢 `locale` 和 `category`所指定的部分或所有目前的程式地區設定資訊。 `locale` 會參考位置 (國家/地區和語言) 來讓您自訂程式的某些方面。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。 如果您將 `locale` 設定為具有電腦上支援之多種形式語言的預設字串，您應檢查 `setlocale` 傳回值以查看是哪種語言生效。 例如，如果您將 `locale` 設定為「中文」，傳回值就有可能是「簡體中文」或「繁體中文」。  
  
 `_wsetlocale` 是 `setlocale` 的寬字元版本，`locale` 引數與 `_wsetlocale` 的傳回值是寬字元字串。 否則，`_wsetlocale` 和 `setlocale` 的行為即會相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsetlocale`|`setlocale`|`setlocale`|`_wsetlocale`|  
  
 `category` 引數會指定程式地區設定資訊中受影響的部分。 用於 `category` 的巨集以及所影響的程式部分如下：  
  
 `LC_ALL`  
 下列清單中的所有分類。  
  
 `LC_COLLATE`  
 `strcoll`、`_stricoll`、`wcscoll`、`_wcsicoll`、`strxfrm`、`_strncoll`、`_strnicoll`、`_wcsncoll`、`_wcsnicoll` 以及 `wcsxfrm` 函式。  
  
 `LC_CTYPE`  
 字元處理函式 (除了 `isdigit`、`isxdigit`、`mbstowcs` 和 `mbtowc`，這些不會受到影響)。  
  
 `LC_MONETARY`  
 `localeconv` 函式傳回的貨幣格式資訊。  
  
 `LC_NUMERIC`  
 由 `printf` 所傳回適用於格式化輸出常式 (如 `localeconv`)、資料轉換常式和非貨幣格式化資訊的小數點字元。 除了小數點字元以外，`LC_NUMERIC` 也會設定由 [localeconv](../../c-runtime-library/reference/localeconv.md) 傳回的千位分隔符號和群組控制字串。  
  
 `LC_TIME`  
 `strftime` 和 `wcsftime` 函式。  
  
 此函式會驗證分類參數。 如果分類參數不是前表中所指定的其中一個值，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會將 `errno` 設定為 `EINVAL` 並傳回 `NULL`。  
  
 `locale` 引數是指向會指定地區設定的字串指標。 如需 `locale` 引數格式的資訊，請參閱[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 如果 `locale` 指向空字串，地區設定即是由實作環境決定的原生環境。 `C` 的值會指定符合 C 轉譯環境的最小 ANSI。 `C` 地區設定會假設所有 `char` 資料類型皆為 1 個位元組，而其值永遠小於 256。  
  
 在程式啟動時，將執行與下列陳述式相同的動作：  
  
 `setlocale( LC_ALL, "C" );`  
  
 `locale` 引數可以讀取地區設定名稱、語言字串、語言字串和國家/地區碼、字碼頁或語言字串、國家/地區碼和字碼頁。 可用的地區設定名稱、語言、國家/地區碼和字碼頁的集合，包含所有 Windows NLS 應用程式開發介面 (API) 支援的所有項目，但不包含每個字元需要超過兩個位元組 (例如 UTF-7 及 UTF-8) 的字碼頁。 如果您提供 UTF-7 或 UTF-8 的字碼頁的值，則 `setlocale` 將會失敗，並傳回 NULL。 `setlocale` 所支援的地區設定名稱集合說明於[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中。 `setlocale` 所支援的語言和國家/地區字串集合列於[語言字串](../../c-runtime-library/language-strings.md)和[國家/地區字串](../../c-runtime-library/country-region-strings.md)中。 我們建議使用內嵌於程式碼或針對儲存體序列化之地區設定字串的效能與維護所適用的地區設定名稱格式。 地區設定名稱字串比語言和國家/地區名稱格式更不容易被作業系統更新變更。  
  
 當 `locale` 引數呼叫 `setlocale` 查詢而非設定國際環境時所傳遞的 null 指標。 如果 `locale` 引數為 null 指標，則不會變更程式目前的地區設定。 相反地，`setlocale` 會傳回與執行緒目前地區設定的 `category` 相關聯的字串指標。 如果 `category` 引數是 `LC_ALL`，函式會傳回表示每種分類之目前設定的字串，並以分號隔開。 例如，呼叫的順序  
  
 `// Set all categories and return "en-US"`  
  
 `setlocale(LC_ALL, "en-US");`  
  
 `// Set only the LC_MONETARY category and return "fr-FR"`  
  
 `setlocale(LC_MONETARY, "fr-FR");`  
  
 `printf("%s\n", setlocale(LC_ALL, NULL));`  
  
 傳回  
  
 `LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US`  
  
 其為與 `LC_ALL` 分類相關聯的字串。  
  
 下列範例與 `LC_ALL` 分類相關。 字串「.OCP」或「.ACP」可以用來以分別指定使用者預設 OEM 字碼頁以及使用者預設 ANSI 字碼頁的用途，字碼頁編號則無法這麼做。  
  
 `setlocale( LC_ALL, "" );`  
 將地區設定設定為從作業系統取得的使用者預設 ANSI 字碼頁的預設值。  
  
 `setlocale( LC_ALL, ".OCP" );`  
 將地區設定明確設定為從作業系統取得的目前 OEM 字碼頁。  
  
 `setlocale( LC_ALL, ".ACP" );`  
 將地區設定設定為從作業系統取得的 ANSI 字碼頁。  
  
 `setlocale( LC_ALL, "<localename>" );`  
 將地區設定設為 \<地區設定名稱> 所表示的地區設定名稱。  
  
 `setlocale( LC_ALL, "<language>_<country>" );`  
 將地區設定設定為 \<語言> 和 \<國家/地區> 所表示的語言和國家/地區，以及從主機作業系統取得的預設字碼頁。  
  
 `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`  
 將地區設定設定為 \<語言>、\<國家/地區> 和<字碼頁>  字串所表示的語言、國家/地區和字碼頁。 您可以使用各種語言、國家/地區和字碼頁的組合。 例如，此呼叫會以字碼頁 1252 將地區設定設為加拿大法文：  
  
 `setlocale( LC_ALL, "French_Canada.1252" );`  
  
 此呼叫會以預設 ANSI 字碼頁將地區設定設為加拿大法文：  
  
 `setlocale( LC_ALL, "French_Canada.ACP" );`  
  
 此呼叫會以預設 OEM 字碼頁將地區設定設為加拿大法文：  
  
 `setlocale( LC_ALL, "French_Canada.OCP" );`  
  
 `setlocale( LC_ALL, "<language>" );`  
 將地區設定設定為\<語言>  所表示的語言，並使用指定語言的預設國家/地區，以及從主機作業系統取得之該國家/地區的使用者預設 ANSI 字碼頁。 舉例而言，下列對 `setlocale` 的呼叫功能是相同的：  
  
 `setlocale( LC_ALL, "en-US" );`  
  
 `setlocale( LC_ALL, "English" );`  
  
 `setlocale( LC_ALL, "English_United States.1252" );`  
  
 我們建議用於效能和維護的第一個格式。  
  
 `setlocale( LC_ALL, ".<code_page>" );`  
 將字碼頁設定為 <字碼頁> 所表示的值，以及指定字碼頁的預設國家/地區和語言 (由主機作業系統所定義)。  
  
 分類必須是 `LC_ALL` 或 `LC_CTYPE` 兩者之一，以促使字碼頁變更。 舉例而言，如果主機作業系統的預設國家/地區和語言是「美國」和「英語」，則下列兩個對 `setlocale` 的呼叫的功能相同：  
  
 `setlocale( LC_ALL, ".1252" );`  
  
 `setlocale( LC_ALL, "English_United States.1252");`  
  
 如需詳細資訊，請參閱 [C/C++ 前置處理器參考](../../preprocessor/c-cpp-preprocessor-reference.md)中的 [setlocale](../../preprocessor/setlocale.md) pragma 指示詞。  
  
 [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md) 函式是用來控制 `setlocale` 會影響在程式中所有執行緒的地區設定，還是只會影響呼叫執行緒的地區設定。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`setlocale`|\<locale.h>|  
|`_wsetlocale`|\<locale.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
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
  
    // Configure per-thread locale to cause all subsequently created   
    // threads to have their own locale.  
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
  
## <a name="see-also"></a>請參閱  
 [地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [_create_locale、_wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)