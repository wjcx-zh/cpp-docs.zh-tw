---
title: "_ismbc 常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ismbc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbc 常式"
  - "ismbc 常式"
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbc 常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每一個**\_ismbc** 常式都會測試指定的多位元組字元`c`是否符合特定的條件。  
  
|||  
|-|-|  
|[\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|  
|[\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[\_ismbclegal、\_ismbclegal\_l、\_ismbcsymbol、\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|  
|[\_ismbchira、\_ismbchira\_l、\_ismbckata、\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|  
  
## 備註  
 每個 **\_ismbc** 常式測試結果實際取決於多位元組字碼頁。  多位元組字碼頁具有單一位元組字母字元。  根據預設，多位元組字碼頁設定為在程式啟動的作業系統取得的系統預設 ANSI 字碼頁。  您可以查詢或變更多位元組字碼頁在使用中分別使用 [\_getmbcp](../c-runtime-library/reference/getmbcp.md) 或 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響。如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些函式沒有以 **\_l** 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以**\_l** 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  
  
|常式|測試條件|字碼頁 932 範例|  
|--------|----------|----------------|  
|[\_ismbcalnum， \_ismbcalnum\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英數字元。|只有當 `c` 是 ASCII 英文字母的單一位元組表示才傳回非零：請參閱範例 `_ismbcdigit` 和 `_ismbcalpha`。|  
|[\_ismbcalpha， \_ismbcalpha\_](../c-runtime-library/reference/ismbcalnum-functions.md)|字母順序|只有當 `c` 是 ASCII 英文字母的單一位元組表示才傳回非零：請參閱`_ismbcupper` 與 `_ismbclower`;或片假名字母:0xA6\<\=`c`\<\=0xDF。|  
|[\_ismbcdigit， \_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|數字|只有當 `c` 是 ASCII 數字的單一位元組表示才傳回非零：0x30\=\<`c`\<\=0x39。|  
|[\_ismbcgraph， \_ismbcgraph\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|圖形|傳回非零只有當 `c` 代表任何 ASCII 控制項或片假名可列印字元除了泛空白字元 \( \)的單一位元組。  如需`_ismbcdigit`、`_ismbcalpha`和`_ismbcpunct`相關範例，請參閱範例。|  
|[\_ismbclegal， \_ismbclegal\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有效的多位元組字元|只有在`c`的第一個位元組範圍為 0x81 – 0x9F 之間或 0xE0 – 0xFC 之間，而第二個位元組位於範圍 0x40 \- 0x7E 或 0x80 \- FC 之間才會傳回非零值。|  
|[\_ismbclower， \_ismbclower\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小寫字母|傳回非零，在只有當 `c` 是 ASCII 小寫英文字母的單一位元組表示：0x61\=\<`c`\<\=0x7A。|  
|[\_ismbcprint， \_ismbcprint\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可列印的|傳回非零只有當 `c` 可以是任何 ASCII 控制項可列印字元的單一位元組表示包含泛空白字元 \(\):提供 `_ismbcspace`、 `_ismbcdigit`、 `_ismbcalpha`和 `_ismbcpunct`參閱範例。|  
|[\_ismbcpunct， \_ismbcpunct\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|標點符號|傳回非零只有當 `c` 可以是任何 ASCII 或片假名標點符號的單一位元組表示。|  
|[\_ismbcblank， \_ismbcblank\_l，](../c-runtime-library/reference/ismbcgraph-functions.md)|空格或水平索引標籤|傳回非零只有當 `c` 是空格字元或水平索引標籤定位字元的單一位元組表示: `c`\=0x20或 `c` \=0x09。|  
|[\_ismbcspace， \_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|傳回非零只有當 `c` 是空白字元: `c`\=0x20 或 0x09\=\<`c`\<\=0x0D。|  
|[\_ismbcsymbol， \_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|多位元組的符號|只有在 0x8141\=\<`c`\<\=0x81AC時才會傳回非零值。|  
|[\_ismbcupper， \_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大寫字母|傳回非零，在只有當 `c` 是 ASCII 大寫英文字母的單一位元組表示：0x41\=\<`c`\<\=0x5A。|  
  
 **字碼頁 932 特定**  
  
 下列常式特有的字碼頁 932。  
  
|常式|測試條件 \(唯獨字碼頁 932\)|  
|--------|------------------------|  
|[\_ismbchira， \_ismbchira\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|雙位元組平假名:0x829F\=\<`c`\<\=0x82F1。|  
|[\_ismbckata， \_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|雙位元組片假名:0x8340\=\<`c`\<\=0x8396。|  
|[\_ismbcl0， \_ismbcl0\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 非漢字:0x8140\=\<`c`\<\=0x889E。|  
|[\_ismbcl1， \_ismbcl1\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 層級 1:0x889F\=\<`c`\<\=0x9872。|  
|[\_ismbcl2， \_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 層級 2:0x989F\=\<`c`\<\=0xEA9E。|  
  
 `_ismbcl0`、 `_ismbcl1`和 `_ismbcl2` 檢查指定值 `c` 符合上表中說明的測試條件，但是不檢查 `c` 是有效的多位元組字元。  如果低位元組範圍 0x00 – 0x3F、0x7F 或 0xFD – 0xFF，這些函式會傳回非零的值，表示字元符合測試條件。  使用 [\_ismbbtrail、\_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 測試多位元組字元是否已定義。  
  
 **END 字碼頁 932 特定**  
  
## 請參閱  
 [字元分類](../c-runtime-library/character-classification.md)   
 [is、isw 常式](../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 常式](../c-runtime-library/ismbb-routines.md)