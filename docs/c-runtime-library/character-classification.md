---
title: 字元分類 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types.character
dev_langs:
- C++
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4c194432c3d7442677a78046ac893e5e3e2a7ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101341"
---
# <a name="character-classification"></a>字元分類

這些每個常式都會測試指定的單一位元組字元、寬字元或滿足條件的多位元組字元。 (根據定義，介於 0 到 127 之間的 ASCII 字元集是所有多位元組字元集的子集。 例如，日文片假名包括 ASCII 以及非 ASCII 字元)。

測試條件會受到地區設定的 **LC_CTYPE** 分類設定影響；如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。

這些常式的執行速度通常會比您撰寫的測試還快，而且也較受到喜好。 例如，下列程式碼執行得比呼叫 `isalpha(c)` 還慢：

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>字元分類常式

|常式傳回的值|字元測試條件|
|-------------|------------------------------|
|[isalnum、iswalnum, _isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)、[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英數字元|
|[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英數字元|
|[isalpha、iswalpha、_isalpha_l、_iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)、[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母順序|
|[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[isblank、iswblank、_isblank_l、_iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)、[_ismbcsblank、_ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白 (空格或水平 Tab)|
|[iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|控制項|
|[iscsym、iscsymf、__iscsym、\__iswcsym、\__iscsymf、\__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|字母、底線或數字|
|[iscsym、iscsymf、__iscsym、\__iswcsym、\__iscsymf、\__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|字母或底線|
|[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)、[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|十進位數字|
|[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|除了空格以外其他均可列印|
|[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)、[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小寫|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|平假名|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|片假名|
|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|合法的多位元組字元|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本層級 0 多位元組字元|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本層級 1 多位元組字元|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本層級 2 多位元組字元|
|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|非英數字元的多位元組字元|
|[isprint、iswprint、_isprint_l、_iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可列印|
|[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|標點符號|[System::Char::IsPunctuation](https://msdn.microsoft.com/library/system.char.ispunctuation.aspx)|
|[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白字元|[System::Char::IsWhiteSpace](https://msdn.microsoft.com/library/system.char.iswhitespace.aspx)|
|[Isupper、iswupper](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)、[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大寫|
|[_isctype、iswctype、_isctype_l、_iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|*desc* 引數指定的屬性|
|[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|十六進位數字|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|傳回有效多位元組字元的長度。結果取決於目前地區設定的 **LC_CTYPE** 分類設定|

## <a name="see-also"></a>請參閱

[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>