---
title: 多位元組字元序列的解譯
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 7431f0c63df60414af192ea38103318c775c430d
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811084"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>多位元組字元序列的解譯

Microsoft 執行階段程式庫中大部分的多位元組字元常式，都能識別與多位元組字碼頁相關的多位元組字元序列。 輸出值會受到地區設定的**LC_CTYPE**分類設定影響。 如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 **_l**尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定。 具有 **_l**尾碼的版本相同，不同之處在于它們使用地區設定參數，而不是目前的地區設定。

## <a name="locale-dependent-multibyte-routines"></a>與地區設定相關的多位元組常式

|常式傳回的值|請使用|
|-------------|---------|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|驗證並傳回多位元組字元的位元組數目|
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|針對多位元組字元字串︰驗證字串中的每個字元；傳回字串長度。 針對寬字元字串：傳回字串長度。|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|將多位元組字元序列轉換為對應的寬字元序列|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|將多位元組字元轉換為對應的寬字元|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|將寬字元序列轉換為對應的多位元組字元序列|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|將寬字元轉換為對應的多位元組字元|

## <a name="locale-independent-multibyte-routines"></a>與地區設定無關的多位元組常式

|常式傳回的值|請使用|
|-------------|---------|
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|將多位元組 UTF-8 字元轉換為對等的 UTF-16 或 UTF-32 字元|
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|將 UTF-16 或 UTF-32 字元轉換為對等的 UTF-8 多位元組字元|

## <a name="see-also"></a>請參閱

[國際化](../c-runtime-library/internationalization.md)\
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
