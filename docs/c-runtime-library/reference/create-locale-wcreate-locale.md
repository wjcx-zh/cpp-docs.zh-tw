---
title: "_create_locale、_wcreate_locale | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff6254ecd33dfc844108b76fc1644eff2a373aed
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="createlocale-wcreatelocale"></a>_create_locale、_wcreate_locale
建立地區設定物件。  
  
## <a name="syntax"></a>語法  
  
```  
_locale_t _create_locale(  
   int category,  
   const char *locale   
);  
_locale_t _wcreate_locale(  
   int category,  
   const wchar_t *locale   
);  
```  
  
#### <a name="parameters"></a>參數  
 `category`  
 分類。  
  
 `locale`  
 地區設定指定名稱。  
  
## <a name="return-value"></a>傳回值  
 如果指定有效的 `locale` 和 `category`，則會以 `_locale_t` 物件傳回指定的地區設定。 但不會變更程式的目前地區設定。  
  
## <a name="remarks"></a>備註  
 `_create_locale` 函式可讓您建立代表某些特定地區設定的物件，以供許多 CRT 函式 (尾碼為 `_l` 的函式) 的特定地區設定版本使用。 此行為類似於 `setlocale`，但不會將指定的地區設定套用至目前的環境，而是將設定儲存在傳回的 `_locale_t` 結構中。 如果不再需要 `_locale_t` 結構，應使用 [_free_locale](../../c-runtime-library/reference/free-locale.md) 予以釋放。  
  
 `_wcreate_locale` 是寬字元版本的 `_create_locale`；`locale` 的 `_wcreate_locale` 引數是寬字元字串。 否則，`_wcreate_locale` 和 `_create_locale` 的行為即會相同。  
  
 `category` 引數會指定特定地區設定行為中受影響的部分。 用於 `category` 的旗標以及所影響的程式部分如下表所示。  
  
 `LC_ALL`  
 所有分類，如下所示。  
  
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
  
 這個函式會驗證 `category` 和 `locale` 參數。 如果分類參數不是上表所提供的任何一個值，或如果 `locale` 為 `NULL`，則函式會傳回 `NULL`。  
  
 `locale` 引數是指向會指定地區設定的字串指標。 如需 `locale` 引數格式的資訊，請參閱[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。  
  
 `locale` 引數可以讀取地區設定名稱、語言字串、語言字串和國家/地區碼、字碼頁或語言字串、國家/地區碼和字碼頁。 可用的地區設定名稱、語言、國家/區域碼和字碼頁的集合，包含 Windows NLS API 支援的所有項目，但不包含每個字元需要超過兩個位元組 (例如 UTF-7 及 UTF-8) 的字碼頁。 如果您提供 UTF-7 或 UTF-8 等字碼頁，則 `_create_locale` 將會失敗，並傳回 NULL。 `_create_locale` 所支援的地區設定名稱集合的說明，位於[地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中。 `_create_locale` 所支援的語言和國家/地區字串集合，列於[語言字串](../../c-runtime-library/language-strings.md)和[國家/地區字串](../../c-runtime-library/country-region-strings.md)中。  
  
 如需地區設定的詳細資訊，請參閱 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 已取代此函式的舊名稱 `__create_locale` (含兩個前置底線)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_create_locale`|\<locale.h>|  
|`_wcreate_locale`|\<locale.h> 或 \<wchar.h>|  
  
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
  
## <a name="see-also"></a>請參閱  
 [地區設定名稱、語言和國家/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [語言字串](../../c-runtime-library/language-strings.md)   
 [國家/地區字串](../../c-runtime-library/country-region-strings.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)   
 [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)