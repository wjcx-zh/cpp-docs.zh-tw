---
title: _ismbb 常式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _ismbb
- ismbb
dev_langs:
- C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c686da7d800725d143d7e3cad9d40e7b0ceb959
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392493"
---
# <a name="ismbb-routines"></a>_ismbb 常式
使用目前的地區設定或指定的 LC_CTYPE 轉換狀態分類，測試指定的整數值 `c` 是否符合特定條件。  
  
|||  
|-|-|  
|[_ismbbalnum、_ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint、_ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|  
|[_ismbbalpha、_ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct、_ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|  
|[_ismbbblank、_ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead、_ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|  
|[_ismbbgraph、_ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint、_ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|  
|[_ismbbkalnum、_ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct、_ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|  
|[_ismbbkana、_ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|  
  
## <a name="remarks"></a>備註  
 `_ismbb` 系列中的每個常式會測試指定的整數值 `c` 是否符合特定條件。 測試結果取決於作用的多位元組字碼頁。 根據預設，多位元組字碼頁會設定為在程式啟動時從作業系統取得的 ANSI 字碼頁。 您可以使用 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 查詢使用中的多位元組字碼頁，或使用 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 加以變更。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 沒有 **_l** 後置字元的函式版本會使用目前的地區設定，來處理這個地區設定的相關行為；具有 **_l** 後置字元的版本均相同，但會改用傳入的地區設定參數。  
  
 `_ismbb` 系列中的常式會依照下列方式來測試指定的整數 `c` 。  
  
|常式傳回的值|位元組測試條件|  
|-------------|-------------------------|  
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|  
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|與 `_ismbbprint`相同，但 `_ismbbgraph` 不包含空格字元 (0x20)。|  
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|標點符號以外的非 ASCII 文字符號。 例如，僅限字碼頁 932， `_ismbbkalnum` 會測試片假名英數字元。|  
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|片假名 (0xA1 - 0xDF)。 僅限字碼頁 932。|  
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII 文字符號或非 ASCII 標點符號。 例如，僅限字碼頁 932，`_ismbbkprint` 會測試片假名英數字元或片假名標點符號 (範圍：0xA1 - 0xDF)。|  
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|非 ASCII 標點符號。 例如，只在字碼頁 932 中的片假名標點符號之 `_ismbbkpunct` 測試。|  
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|多位元組字元的第一個位元組 例如，僅限在字碼頁 932 中，有效範圍是 0x81 - 0x9F 和 0xE0 - 0xFC。|  
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** 包含空格字元 (0x20)。|  
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|  
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|多位元組字元的第二個位元組 例如，僅限在字碼頁 932 中，有效範圍是 0x40 - 0x7E 和 0x80 - 0xEC。|  
  
 下表顯示撰寫這些常式之測試條件的 ORed 值。 資訊清單常數 `_BLANK`、 `_DIGIT`、 `_LOWER`、 `_PUNCT`和 `_UPPER` 是在 Ctype.h 中所定義。  
  
|常式傳回的值|_BLANK|_DIGIT|LOWER|_PUNCT|UPPER|非<br /><br /> ASCII<br /><br /> 文字|非<br /><br /> ASCII<br /><br /> punct|  
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|  
|`_ismbbalnum`|—|x|x|—|x|x|—|  
|`_ismbbalpha`|—|—|x|—|x|x|—|  
|`_ismbbblank`|x|—|—|—|—|—|—|  
|`_ismbbgraph`|—|x|x|x|x|x|x|  
|`_ismbbkalnum`|—|—|—|—|—|x|—|  
|`_ismbbkprint`|—|—|—|—|—|x|x|  
|`_ismbbkpunct`|—|—|—|—|—|—|x|  
|`_ismbbprint`|x|x|x|x|x|x|x|  
|`_ismbbpunct`|—|—|—|x|—|—|x|  
  
 `_ismbb` 常式可當作函式和巨集來實作。 如需如何選擇實作的詳細資訊，請參閱[在函式和巨集之間選擇的建議](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。  
  
## <a name="see-also"></a>請參閱  
 [位元組分類](../c-runtime-library/byte-classification.md)   
 [is、isw 常式](../c-runtime-library/is-isw-routines.md)   
 [_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)