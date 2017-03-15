---
title: "地區設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.international"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "國家/地區資訊"
  - "語言資訊常式"
  - "地區設定常式"
  - "當地語系化, 地區設定"
  - "setlocale 函式"
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# 地區設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*地區設定* 是指您可使用自訂程式的國家\/地區及語言設定。  有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。  如需詳細資訊，請參閱[地區設定分類](../c-runtime-library/locale-categories.md)。  
  
 當使用沒有 `_l` 後置字元的函式時，請使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函式變更或查詢的部分或所有目前的程式或執行緒的地區設定資訊。  只在特定函式執行的期間，與 `_l` 尾碼的函式會使用地區設定參數傳入資訊。  若要建立一個地區設定為具有函式搭配 `_l` 後置字元，請使用 [\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)。  若要釋放這個地區設定，請使用 [\_free\_locale](../c-runtime-library/reference/free-locale.md)。  若要取得目前的地區設定，請使用 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)。  
  
 使用 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 控制是否每個執行緒有自己的地區設定或是所有在相同程式中的執行緒共享同樣的地區設定。  如需詳細資訊和範例程式碼，請參閱 [地區設定和程式碼頁面](../text/locales-and-code-pages.md)。  
  
 下表有更多可用的函式安全版，由 `_s` \(安全版\)\) 尾碼表示。  如需詳細資訊，請參閱[CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
### 地區設定相依的常式  
  
|常式|使用|`setlocale` 類別設定相關屬性|  
|--------|--------|--------------------------|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|轉換字元至浮點數|`LC_NUMERIC`|  
|[atoi、\_atoi\_l、\_wtoi、\_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|轉換字元至整數|`LC_NUMERIC`|  
|[\_atoi64、\_atoi64\_l、\_wtoi64、\_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|轉換字元至64位元整數|`LC_NUMERIC`|  
|[atol、\_atol\_l、\_wtol、\_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|轉換字元至 long 型別的值|`LC_NUMERIC`|  
|[\_atodbl、\_atodbl\_l、\_atoldbl、\_atoldbl\_l、\_atoflt、\_atoflt\_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|轉換字元至 double\-long 型別的值|`LC_NUMERIC`|  
|[is 常式](../c-runtime-library/is-isw-routines.md)|在特定情況下給予整數的測試。|`LC_CTYPE`|  
|[isleadbyte、\_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|前導位元組的測試|`LC_CTYPE`|  
|[localeconv](../c-runtime-library/reference/localeconv.md)|讀取格式化的數字數量的適當值。|`LC_MONETARY, LC_NUMERIC`|  
|[MB\_CUR\_MAX](../c-runtime-library/mb-cur-max.md)|最大長度 \(以位元組任何多位元組字元在目前地區設定 \(在 STDLIB.H\) \)定義的巨集|`LC_CTYPE`|  
|[\_mbccpy、\_mbccpy\_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[\_mbccpy\_s、\_mbccpy\_s\_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|複製一個多位元組字元|`LC_CTYPE`|  
|[\_mbclen、mblen、\_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|驗證並傳回以多位元表示的位元組數目|`LC_CTYPE`|  
|[strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|對於多位元組字元字串:驗證字串中的每個字元;傳回字串的長度。|`LC_CTYPE`|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|轉換多位元組字元序列至對應的寬字元序列|`LC_CTYPE`|  
|[mbtowc、\_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|轉換多位元組字元至對應的寬字元|`LC_CTYPE`|  
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式|寫入格式化輸出|`LC_NUMERIC` \(判斷基底字元輸出\)|  
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函式|讀取格式輸入|`LC_NUMERIC` \(判斷基底字元辨識\)|  
|[setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|為應用程式設定\(地區設定\)|不適用|  
|[strcoll、wcscoll、\_mbscoll、\_strcoll\_l、\_wcscoll\_l、\_mbscoll\_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|比較兩個字串的字元|`LC_COLLATE`|  
|[\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|不考慮大小寫的比較兩個字串|`LC_CTYPE`|  
|[\_stricoll、\_wcsicoll、\_mbsicoll、\_stricoll\_l、\_wcsicoll\_l、\_mbsicoll\_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|比較兩個字串的字元 \(不區分大小寫\)|`LC_COLLATE`|  
|[\_strncoll、\_wcsncoll、\_mbsncoll、\_strncoll\_l、\_wcsncoll\_l、\_mbsncoll\_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|比較兩個字串第 `n` 個字元|`LC_COLLATE`|  
|[\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|不考慮大小寫的比較兩個字串的字元。|`LC_CTYPE`|  
|[\_strnicoll、\_wcsnicoll、\_mbsnicoll、\_strnicoll\_l、\_wcsnicoll\_l、\_mbsnicoll\_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|比較兩個字串第 `n`個字元 \(不區分大小寫\)|`LC_COLLATE`|  
|[strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|根據提供的 `format` 引數格式化日期和時間值|`LC_TIME`|  
|[\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|在正確的地方，轉換每個大寫字母至小寫字母|`LC_CTYPE`|  
|[strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|轉換字元字串至 `double` 值。|`LC_NUMERIC` \(判斷基底字元辨識\)|  
|[strtol、wcstol、\_strtol\_l、\_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|轉換字元字串至 `long` 值|`LC_NUMERIC` \(判斷基底字元辨識\)|  
|[strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|將字串轉換成不帶正負號的長整數值|`LC_NUMERIC` \(判斷基底字元辨識\)|  
|[\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|在正確的地方，轉換每個小寫字母至大寫字母|`LC_CTYPE`|  
|[strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|轉換成字串自動分頁的表單根據地區設定|`LC_COLLATE`|  
|[tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|轉換指定字元對應的小寫字母|`LC_CTYPE`|  
|[toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|轉換指定字元對應的大寫字母。|`LC_CTYPE`|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|轉換寬字元序列至對應的多位元組字元序列|`LC_CTYPE`|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|轉換寬字元至對應的多位元組字元|`LC_CTYPE`|  
  
> [!NOTE]
>  對於多位元組常式，多位元組字碼頁必須和有[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)的地區設定相等 。  有 `_MB_CP_LOCALE` 引數的[\_setmbcp](../c-runtime-library/reference/setmbcp.md)使多位元字碼頁和 `setlocale` 字碼頁相同。  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)