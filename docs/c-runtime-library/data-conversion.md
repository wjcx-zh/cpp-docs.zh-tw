---
title: "資料轉換 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11b28793e5e659e3135061e3a6fd410d9b1c9f3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-conversion"></a>資料轉換
這些常式會將資料從一種形式轉換成另一種形式。 這些常式的執行速度通常比您撰寫的轉換還快。 開頭為 `to` 前置詞的每個常式都會實作為函式和巨集。 如需選擇實作的資訊，請參閱[選擇函式與巨集](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。  
  
### <a name="data-conversion-routines"></a>資料轉換常式  
  
|常式傳回的值|使用|  
|-------------|---------|  
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找整數的絕對值|  
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將字串轉換為 `float`|  
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|將字串轉換為 `int`|  
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|將字串轉換為 `__int64`|  
|[atol、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|將字串轉換為 `long`|  
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|將 UTF-16 或 UTF-32 字元轉換為對等的多位元組字元|  
|[_ecvt](../c-runtime-library/reference/ecvt.md)、[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|將 `double` 轉換為指定長度的字串|  
|[_fcvt](../c-runtime-library/reference/fcvt.md)、[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|將 `double` 轉換為小數點後具有指定位數的字串|  
|[_gcvt](../c-runtime-library/reference/gcvt.md)、[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|將 `double` 數字轉換為字串；將字串儲存在緩衝區|  
|[_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)、[_itoa_s、_i64toa_s、_ui64toa_s、_itow_s、_i64tow_s、_ui64tow_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|將 `int` 或 `__int64` 轉換為字串|  
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找 `long` 整數的絕對值|  
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找 `long long` 整數的絕對值|  
|[_ltoa、_ltow](../c-runtime-library/reference/ltoa-ltow.md)、[_ltoa_s、_ltow_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|將 `long` 轉換為字串|  
|[_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|將 1 個位元組的多位元組字元轉換為對應的 2 個位元組的多位元組字元|  
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|將日本工業標準 (JIS) 字元轉換為日本 Microsoft (JMS) 字元|  
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|將 JMS 字元轉換為 JIS 字元|  
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|將多位元組字元轉換為 1 個位元組平假名碼|  
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|將多位元組字元轉換為 1 個位元組片假名碼|  
|[_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|將 2 個位元組的多位元組字元轉換為對應之 1 個位元組的多位元組字元|  
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|將多位元組字元轉換為對等的 UTF-16 或 UTF-32 字元|  
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|將多位元組字元序列轉換為對應的寬字元序列|  
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|將多位元組字元轉換為對應的寬字元|  
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|將字串轉換為 `double`|  
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|將字串轉換為 `long` 整數|  
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|將字串轉換為 `unsigned long` 整數|  
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根據地區設定特定資訊，將字串轉換為定序的形式|  
|[toascii、__toascii](../c-runtime-library/reference/toascii-toascii.md)|將字元轉換為 ASCII 碼||  
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|測試字元並轉換為小寫 (如果目前為大寫)|  
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|將字元無條件轉換為小寫|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|  
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|測試字元並轉換為大寫 (如果目前為小寫)|  
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|將字元無條件轉換為大寫|  
|[_ultoa、_ultow](../c-runtime-library/reference/ultoa-ultow.md)、[_ultoa_s、_ultow_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|將 `unsigned long` 轉換為字串|  
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|將寬字元序列轉換為對應的多位元組字元序列|  
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|將寬字元轉換為對應的多位元組字元|  
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將寬字元字串轉換為 `double`|   
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|將寬字元字串轉換為 `int`|  
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|將寬字元字串轉換為 `__int64`|  
|[atol、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|將寬字元字串轉換為 `long`|  
  
## <a name="see-also"></a>請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)