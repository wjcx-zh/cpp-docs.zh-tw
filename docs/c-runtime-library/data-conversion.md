---
title: 資料轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f06153b4c4f037172e96e3ce1222311a82c71772
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="data-conversion"></a>資料轉換

這些常式會將資料從一種形式轉換成另一種形式。 這些常式的執行速度通常比您撰寫的轉換還快。 開頭為 *to* 前置詞的每個常式都會實作為函式和巨集。 如需選擇實作的資訊，請參閱[選擇函式與巨集](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。

## <a name="data-conversion-routines"></a>資料轉換常式

|常式傳回的值|使用|
|-------------|---------|
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找整數的絕對值|
|[atof、_atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將字串轉換為 **float**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|將字串轉換為 **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|將字串轉換為 **__int64** 或 **long long**|
|[atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|將字串轉換為 **long**|
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|將 UTF-16 或 UTF-32 字元轉換為對等的多位元組字元|
|[_ecvt](../c-runtime-library/reference/ecvt.md)、[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|將 **double** 轉換為指定長度的字串|
|[_fcvt](../c-runtime-library/reference/fcvt.md)、[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|將 **double** 轉換為小數點後具有指定位數的字串|
|[_gcvt](../c-runtime-library/reference/gcvt.md)、[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|將 **double** 數字轉換為字串；將字串儲存在緩衝區|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|將整數型別轉換成字串|
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找 **long** 整數的絕對值|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|尋找 **long long** 整數的絕對值|
|[_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|將 1 個位元組的多位元組字元轉換為對應的 2 個位元組的多位元組字元|
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|將日本工業標準 (JIS) 字元轉換為日本 Microsoft (JMS) 字元|
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|將 JMS 字元轉換為 JIS 字元|
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|將多位元組字元轉換為 1 個位元組平假名碼|
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|將多位元組字元轉換為 1 個位元組片假名碼|
|[_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|將 2 個位元組的多位元組字元轉換為對應之 1 個位元組的多位元組字元|
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|將多位元組字元轉換為對等的 UTF-16 或 UTF-32 字元|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|將多位元組字元序列轉換為對應的寬字元序列|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|將多位元組字元轉換為對應的寬字元|
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|將字串轉換成 **double**|
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|將字串轉換為 **long** 整數|
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|將字串轉換為 **unsigned long** 整數|
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根據地區設定特定資訊，將字串轉換為定序的形式|
|[toascii、__toascii](../c-runtime-library/reference/toascii-toascii.md)|將字元轉換為 ASCII 碼||
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|測試字元並轉換為小寫 (如果目前為大寫)|
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|將字元無條件轉換為小寫|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|測試字元並轉換為大寫 (如果目前為小寫)|
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|將字元無條件轉換為大寫|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|將寬字元序列轉換為對應的多位元組字元序列|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|將寬字元轉換為對應的多位元組字元|
|[_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將寬字元字串轉換為 **double**|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|將寬字元字串轉換為 **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|將寬字元字串轉換為 **__int64** 或 **long long**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|將寬字元字串轉換為 **long**|

## <a name="see-also"></a>另請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
