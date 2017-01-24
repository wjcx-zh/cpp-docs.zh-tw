---
title: "位元組分類 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types.bytes"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "位元組分類常式"
  - "位元組, 測試"
  - "字碼頁 932"
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 位元組分類
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些常式中的每一個條件符合測試多位元組字元的指定位元組。  除了指定的位置之外，輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響。如需詳細資訊，請參閱  [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  
  
> [!NOTE]
>  根據定義，0 到 127 的 ASCII 字元集是所有多位元組字元集的子集。  例如，日文片假名字元集包括 ASCII 以及非 ASCII 字元。  
  
 下表的預定義常值定義於 CTYPE.H。  
  
### 多位元組字元位元組分類常式  
  
|常式|位元測試條件|.NET Framework 對等用法|  
|--------|------------|-------------------------|  
|[isleadbyte、\_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|前導位元組；測試結果取決於 `LC_CTYPE` 目前地區設定分類設定|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbalnum、\_ismbbalnum\_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum &#124;&#124; _ismbbkalnum`|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbalpha、\_ismbbalpha\_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|`isalpha &#124;&#124; _ismbbkalnum`|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbgraph、\_ismbbgraph\_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|與 `_ismbbprint`相同，但 `_ismbbgraph` 不包含空白字元 \(0x20\)|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkalnum、\_ismbbkalnum\_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|非 ASCII 除了標點符號以外的文字符號。  例如，只在字碼頁 932 中， `_ismbbkalnum` 會測試片假名英數|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkana、\_ismbbkana\_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|片假名 \(0xA1 – 0xDF\)，字碼頁 932 中|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkprint、\_ismbbkprint\_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII 文字或非 ASCII 標點符號。  例如，只在字碼頁 932 中， `_ismbbkprint` 會測試片假名英數或片假名標點符號 \(範圍:0xA1 – 0xDF\)。|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkpunct、\_ismbbkpunct\_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|非 ASCII 的點。  例如，在字碼頁 932 中， `_ismbbkpunct` 會測試片假名標點符號。|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbblead、\_ismbblead\_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|第一個位元組的多位元組字元。  例如，在字碼頁 932 中，有效範圍是 0x81 – 0x9F， 0xE0 – 0xFC。|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbprint、\_ismbbprint\_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint &#124;&#124; _ismbbkprint. ismbbprint` 包含空白字元 \(0x20\)|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbpunct、\_ismbbpunct\_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct &#124;&#124; _ismbbkpunct`|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbtrail, \_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|第二個位元組多位元組字元。  例如，在字碼頁 932 中，有效範圍是 0x40 – 0x7E， 0x80 – 0xEC。|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbslead, \_ismbslead\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|前導位元組 \(在字串內容\)|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[ismbstrail, \_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|後隨位元組 \(在字串內容\)|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_mbbtype、\_mbbtype\_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|根據上一個位元組的傳回位元組型別|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_mbsbtype、\_mbsbtype\_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|傳回在字串內的位元組型別|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|追蹤多位元組字元轉換的狀態。|不適用，不過請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
  
 `MB_LEN_MAX` 巨集，定義在 LIMITS.H，在所有多位元組字元可能有的位元組擴展至最大長度。  `MB_CUR_MAX`，定義在 STDLIB.H，在位元組擴展至最大長度所有多位元組字元在目前地區設定。  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)