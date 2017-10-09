---
title: "位元組分類 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.types.bytes
dev_langs:
- C++
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 129e549b4151d913cf0ad026faff967d30f87e44
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="byte-classification"></a>位元組分類
這些每個常式都會測試多位元組字元的指定位元組是否滿足條件。 除了另行指定之處，輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 `_l` 後置字元的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 `_l` 後置字元的版本也一樣，只不過它們會改用傳遞的地區設定參數。  
  
> [!NOTE]
>  根據定義，介於 0 到 127 之間的 ASCII 字元是所有多位元組字元集的子集。 例如，日文片假名字元集包括 ASCII 以及非 ASCII 字元。  
  
 下表中的預先定義常數定義於 CTYPE.H 中。  
  
### <a name="multibyte-character-byte-classification-routines"></a>多位元組字元位元組分類常式  
  
|常式|位元組測試條件|  
|-------------|-------------------------|  
|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|前導位元組；測試結果會取決於目前地區設定的 `LC_CTYPE` 分類設定|  
|[_ismbbalnum、_ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum &#124;&#124; _ismbbkalnum`|  
|[_ismbbalpha、_ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|`isalpha &#124;&#124; _ismbbkalnum`|  
|[_ismbbgraph、_ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|與 `_ismbbprint` 相同，但 `_ismbbgraph` 不包含空格字元 (0x20)|  
|[_ismbbkalnum、_ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|標點符號以外的非 ASCII 文字符號。 例如，僅限字碼頁 932，`_ismbbkalnum` 會測試片假名英數字元|  
|[_ismbbkana、_ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|片假名 (0xA1 - 0xDF)，僅限字碼頁 932|  
|[_ismbbkprint、_ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII 文字符號或非 ASCII 標點符號。 例如，僅限字碼頁 932，`_ismbbkprint` 會測試片假名英數字元或片假名標點符號 (範圍：0xA1 - 0xDF)。|  
|[_ismbbkpunct、_ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|非 ASCII 標點符號。 例如，只在字碼頁 932 中的片假名標點符號之 `_ismbbkpunct` 測試。|  
|[_ismbblead、_ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|多位元組字元的第一個位元組 例如，僅限在字碼頁 932 中，有效範圍是 0x81 - 0x9F 和 0xE0 - 0xFC。|  
|[_ismbbprint、_ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint &#124;&#124; _ismbbkprint. ismbbprint` 包含空格字元 (0x20)|  
|[_ismbbpunct、_ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct &#124;&#124; _ismbbkpunct`|  
|[_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|多位元組字元的第二個位元組 例如，僅限在字碼頁 932 中，有效範圍是 0x40 - 0x7E 和 0x80 - 0xEC。|  
|[_ismbslead、_ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|前導位元組 (於字串內容中)|  
|[ismbstrail、_ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|後隨位元組 (於字串內容中)|  
|[_mbbtype、_mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|根據上一個位元組傳回位元組類型|  
|[_mbsbtype、_mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|傳回字串內的位元組類型|  
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|追蹤多位元組字元轉換的狀態。|  
  
 `MB_LEN_MAX` 巨集，定義於 LIMITS.H，會展開至任何多位元組字元可具備的最大長度，以位元組為單位。 `MB_CUR_MAX` 定義於 STDLIB.H，會展開至目前地區設定中任何多位元組字元的最大長度，以位元組為單位。  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
