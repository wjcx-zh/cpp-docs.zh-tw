---
title: "_create_locale、_wcreate_locale | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_create_locale"
  - "__create_locale"
  - "_wcreate_locale"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "create_locale"
  - "_create_locale"
  - "__create_locale"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__create_locale 函式"
  - "_create_locale 函式"
  - "create_locale 函式"
  - "地區設定, 建立"
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _create_locale、_wcreate_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立地區物件。  
  
## 語法  
  
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
  
#### 參數  
 `category`  
 分類  
  
 `locale`  
 地區設定指定名稱  
  
## 傳回值  
 如果有效的 `locale` 和 `category` 被指定，指定的地區設定以 `_locale_t` 物件傳回。  未變更目前程式的目前地區設定。  
  
## 備註  
 `_create_locale` 函式可讓您建立表示某些特定區域設定的物件，可用於許多 CRT 函式 \(有 `_l` 尾碼的函式\) 地區設定特定版本。  行為與 `setlocale`類似，不同的是，非套用至目前環境中指定的地區設定，這些設定被儲存在回傳的 `_locale_t` 結構中。  當不再需要時，應使用 [\_free\_locale](../../c-runtime-library/reference/free-locale.md) 釋放 `_locale_t` 結構。  
  
 `_wcreate_locale` 是 `_create_locale` 的寬字元版本。 `_wcreate_locale` 的 `locale` 引數是寬字元字串。  `_wcreate_locale` 和 `_create_locale` 其餘行為相同。  
  
 `category` 引數指定受影響地區設定特定行為的一部分。  用於 `category` 的旗標和它們會影響程式的部分如下表所示。  
  
 `LC_ALL`  
 所有分類，如下所列。  
  
 `LC_COLLATE`  
 `strcoll`、`_stricoll`、 `wcscoll`、`_wcsicoll`、 `strxfrm`、 `_strncoll`、 `_strnicoll`、 `_wcsncoll`、`_wcsnicoll`、以及 `wcsxfrm`函式。  
  
 `LC_CTYPE`  
 字元處理函式 \(除了 `isdigit`、 `isxdigit`、 `mbstowcs`和 `mbtowc`，這些不會受到影響\)。  
  
 `LC_MONETARY`  
 `localeconv` 函式傳回的貨幣格式資訊。  
  
 `LC_NUMERIC`  
 小數點的字元格式化輸出的常式 \(例如 `printf`\)，則資料轉換常式的和對於非貨幣的格式化資訊由 `localeconv`傳回。  除了十進位點字元以外， `LC_NUMERIC` 設定由 [localeconv](../../c-runtime-library/reference/localeconv.md)傳回的千位分隔符號和群組控制項字串。  
  
 `LC_TIME`  
 `strftime` 以及 `wcsftime`函式。  
  
 這個函式會驗證`category` and `locale` 參數。  如果分類參數不是上表中指定的其中一個值或 `locale` 是 `NULL`，函式會傳回 `NULL`。  
  
 `locale` 引數是指向指定地區設定的字串指標。  如需 `locale` 引數格式的詳細資訊，請參閱 [地區設定名稱、語言和國家\/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。  
  
 `locale` 引數可以讀取地區設定名稱、語言字串、語言字串和國家\/地區碼、字碼頁或語言字串、國家\/地區碼和字碼頁。  可用的地區設定名稱、語言、國家\/地區碼和字碼頁的集合，包含所有Windows NLS 應用程式開發介面所支援的項目，但不包含需要超過每個字元的兩個位元組\(例如 UTF\-7 及 UTF\-8\) 的字碼頁。  如果您提供如UTF\-7 或 UTF\-8 的字碼頁，則 `_create_locale` 將會失敗並傳回 null。  `_create_locale` 支援的地區設定名稱集合在 [地區設定名稱、語言和國家\/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中說明。  `_create_locale` 所支援的語言和國家\/地區字串列在 [語言字串](../../c-runtime-library/language-strings.md) 和 [國家\/地區字串](../../c-runtime-library/country-region-strings.md)中。  
  
 如需地區設定的詳細資訊，請參閱[setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 這個函式`__create_locale` 先前的名稱 \(與兩個前置底線\)，已被取代。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_create_locale`|\<locale.h \- 地區設定\>|  
|`_wcreate_locale`|\<locale.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
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
       //  
       if (!_strftime_l((char *)str, 100, "%#x",   
                     (const struct tm *)&thetime, locale))  
               printf("_strftime_l failed!\n");  
       else  
               printf("In de-CH locale, _strftime_l returns '%s'\n",   
                      str);  
  
       _free_locale(locale);  
  
       // Create a locale object representing the default C locale  
       locale = _create_locale(LC_ALL, "C");  
       time (&ltime);  
       _gmtime64_s(&thetime, &ltime);  
  
       if (!_strftime_l((char *)str, 100, "%#x",   
                     (const struct tm *)&thetime, locale))  
               printf("_strftime_l failed!\n");  
       else  
               printf("In 'C' locale, _strftime_l returns '%s'\n",   
                      str);  
  
       _free_locale(locale);  
}  
```  
  
## 範例輸出  
  
```  
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'  
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'  
```  
  
## .NET Framework 對等用法  
 [System::Globalization::CultureInfo Class](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)  
  
## 請參閱  
 [地區設定名稱、語言和國家\/地區字串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [語言字串](../../c-runtime-library/language-strings.md)   
 [國家\/地區字串](../../c-runtime-library/country-region-strings.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)   
 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)