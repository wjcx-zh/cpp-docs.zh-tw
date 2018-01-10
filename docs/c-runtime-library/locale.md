---
title: "地區設定 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.international
dev_langs: C++
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 835c396c36a23d05a1e3512fa7ad5e4c4e81c795
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="locale"></a>地區設定
「地區設定」指的是可用來自訂程式的國家/地區和語言設定。 有些地區設定相關分類包括日期和貨幣值的顯示格式。 如需詳細資訊，請參閱[地區設定分類](../c-runtime-library/locale-categories.md)。  
  
 使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函式，可在使用沒有 `_l` 尾碼的函式時變更或查詢部分或所有目前程式或執行緒地區設定資訊。 具有 `_l` 尾碼的函式只會使用傳入的地區設定參數，作為其在執行該特定函式期間的地區設定資訊。 若要建立地區設定以與使用 `_l` 尾碼的函式搭配使用，請使用 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)。 若要釋出此地區設定，請使用 [_free_locale](../c-runtime-library/reference/free-locale.md)。 若要取得目前地區設定，請使用 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md)。  
  
 使用 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 來控制每個執行緒都有它自己的地區設定，還是程式中的所有執行緒都共用相同的地區設定。 如需詳細資訊，請參閱[地區設定和字碼頁](../text/locales-and-code-pages.md)。  
  
 下表中有更安全版本的函式可供使用，以 `_s` ("secure") 尾碼表示。 如需詳細資訊，請參閱 [CRT 的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
### <a name="locale-dependent-routines"></a>地區設定相關常式  
  
|常式傳回的值|使用|`setlocale` 分類設定相依性|  
|-------------|---------|---------------------------------------------|  
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將字元轉換為浮點值|`LC_NUMERIC`|  
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|將字元轉換為整數值|`LC_NUMERIC`|  
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|將字元轉換為 64 位元整數值|`LC_NUMERIC`|  
|[atol、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|將字元轉換為 long 值|`LC_NUMERIC`|  
|[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|將字元轉換為 double-long 值|`LC_NUMERIC`|  
|[is 常式](../c-runtime-library/is-isw-routines.md)|測試特定條件的指定整數。|`LC_CTYPE`|  
|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|前導位元組的測試|`LC_CTYPE`|  
|[localeconv](../c-runtime-library/reference/localeconv.md)|讀取用於格式化數值數量的適當值|`LC_MONETARY, LC_NUMERIC`|  
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|目前地區設定中任何多位元組字元的最大長度，以位元組為單位 (定義於 STDLIB.H 中的巨集)|`LC_CTYPE`|  
|[_mbccpy、_mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)、[_mbccpy_s、_mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|複製一個多位元組字元|`LC_CTYPE`|  
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|驗證並傳回多位元組字元的位元組數目|`LC_CTYPE`|  
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|針對多位元組字元字串︰驗證字串中的每個字元；傳回字串長度|`LC_CTYPE`|  
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|將多位元組字元序列轉換為對應的寬字元序列|`LC_CTYPE`|  
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|將多位元組字元轉換為對應的寬字元|`LC_CTYPE`|  
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函式|寫入格式化輸出|`LC_NUMERIC` (判斷基底字元輸出)|  
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函式|讀取格式化輸入|`LC_NUMERIC` (判斷基底字元辨識)|  
|[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|選取程式的地區設定|不適用|  
|[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|比較兩個字串的字元|`LC_COLLATE`|  
|[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|比較兩個字串，而不考慮大小寫|`LC_CTYPE`|  
|[_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|比較兩個字串的字元 (不區分大小寫)|`LC_COLLATE`|  
|[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|比較兩個字串的第一個 `n` 字元|`LC_COLLATE`|  
|[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|比較兩個字串的字元，而不考慮大小寫。|`LC_CTYPE`|  
|[_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|比較兩個字串的第一個 `n` 字元 (不區分大小寫)|`LC_COLLATE`|  
|[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|根據提供的 `format` 引數，格式化日期和時間值|`LC_TIME`|  
|[_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)、[_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|就地將指定字串中的每個大寫字母轉換為小寫|`LC_CTYPE`|  
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|將字元字串轉換為 `double` 值|`LC_NUMERIC` (判斷基底字元辨識)|  
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|將字元字串轉換為 `long` 值|`LC_NUMERIC` (判斷基底字元辨識)|  
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|將字元字串轉換為不帶正負號的 long 值|`LC_NUMERIC` (判斷基底字元辨識)|  
|[_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)、[_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|就地將字串中的每個小寫字母轉換為大寫|`LC_CTYPE`|  
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根據地區設定，將字串轉換為定序的形式|`LC_COLLATE`|  
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|將指定字元轉換為對應的小寫字元|`LC_CTYPE`|  
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|將指定字元轉換為對應的大寫字母|`LC_CTYPE`|  
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|將寬字元序列轉換為對應的多位元組字元序列|`LC_CTYPE`|  
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|將寬字元轉換為對應的多位元組字元|`LC_CTYPE`|  
  
> [!NOTE]
>  針對多位元組常式，多位元組字碼頁必須等同於使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 所設定的地區設定。 引數為 `_MB_CP_LOCALE` 的 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 可讓多位元組字碼頁與 `setlocale` 字碼頁相同。  
  
## <a name="see-also"></a>請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)