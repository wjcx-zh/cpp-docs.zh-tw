---
title: "字串轉換為數值函式 | Microsoft Docs"
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
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcstoui64"
  - "_tcstoi64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "剖析, 數值字串"
  - "字串轉換, 到數值"
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字串轉換為數值函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

-   [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)  
  
-   [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)  
  
-   [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)  
  
-   [\_strtoi64, \_wcstoi64, \_strtoi64\_l, \_wcstoi64\_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)  
  
-   [\_strtoui64、\_wcstoui64、\_strtoui64\_l、\_wcstoui64\_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)  
  
## 備註  
 在 **strtod** 系列的每個函式轉換 null 結尾字串為數值。  可用的函式列在下表。  
  
|功能|說明|  
|--------|--------|  
|`strtod`|轉換字串成雙精確度浮點數值。|  
|`strtol`|將字串轉換成長整數|  
|`strtoul`|將字串轉換成不帶正負號的長整數|  
|`_strtoi64`|將字串轉換成 64 位元的 `__int64` 整數。|  
|`_strtoui64`|將字串轉換為不帶正負號的 16 位元整數。`__int64` integer|  
  
 `wcstod`、 `wcstol`、`wcstoul` 和 `_wcstoi64` 分別為 `strtod`、`strtol`、 `strtoul` 和 `_strtoi64` 的寬字元版本。  對這些寬字元函式的每一個字串引數是寬字元字串；每個函式另有相同的行為與其單一位元組字元對應。  
  
 `strtod` 函式會採用兩個引數：第一個輸入字串和第二個指標結束轉換處理序的字元。  `strtol`、 `strtoul`、 **\_strtoi64** 和 **\_strtoui64** 在轉換處理序會以第三個引數為基數使用。  
  
 輸入字串是可解譯為指定類型的數值的字元序列。   函式會在它無法辨認成數字部分的第一個字元處，停止讀取字串。  這可能是結束的空字元。  對於 `strtol`、 `strtoul`、 `_strtoi64`和 `_strtoui64`，此終止字元可以是第一個數字字元大於或等於使用者提供的基數。  
  
 如果使用者提供的對結束轉換字元的指標不是在呼叫階段設定為 **NULL** ，將儲存停止掃描的字元的指標。  如果轉換無法執行 \(未找到有效的數字或指定了無效基底\)，則字串指標的值會儲存在那個位址。  
  
 `strtod` 必須是下列格式的字串：  
  
 \[*空白*\] \[*標記*\] \[`digits`\] \[**.**`digits`\]\[ {**d** &#124; **D** &#124; **e** &#124; **E**}\[*sign*\]`digits`\]  
  
 *空白鍵* 可能包含空格或定位字元，這些字元會被忽略；*sign* 為加號\(**\+**\) 或減號 \(**–**\)；且 `digits` 是一個或多個十進位數字。  如果基數字元之前沒有數字，則基數字元之後必須至少出現一個數字。  十進位數字後面可以跟著指數，指數包括一個引入字母 \(**d**、**D**、**e** 或 **E**\)\) 和選擇性地一個帶正負號的整數。  如果指數部分或基數字元都沒有出現，則假設字串中最後一個數字後面有基數字元。  第一個不符合這個格式的字元會停止掃描。  
  
 `strtol`、 `strtoul`、 `_strtoi64`和 `_strtoui64` 函式預期下列格式的字串：  
  
 \[*whitespace*\] \[{**\+** &#124; **–**}\] \[**0** \[{ **x** &#124; **X** }\]\] \[`digits`\]  
  
 如果基本引述介於 2 和 36 之間，則會使用它當做數字的底數。  如果是 0，初始字元參考由結束轉換指標用來判斷基底。  如果第一個字元是 0，而第二個字元不是「x」或「X」，字串會解譯為八進位整數；否則，它會被解譯為十進位數字。  如果第一個字元是 '0'，而第二個字元不是「x」或「X」，字串會解譯為十六進位整數。  如果第一個字元是 1' 到 '9'，字串會解譯為十進位整數。  字母 'a' 到 'z' \(或 'A' 到 'Z"\) 被指派值 10 到 35；只允許指派值小於 *基底* 的字母。  `strtoul` 和 `_strtoui64` 允許加號\(**\+**\) 或減號 \(**–**\) 前置字元；前置減號指示傳回值為否定。  
  
 輸出值受地區設定的`LC_NUMERIC` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 **\_l** 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以**\_l** 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  
  
 當這些函式傳回的值會造成溢位或反向溢位，或轉換時，無法執行時，特殊情況傳回值如下所示：  
  
|功能|條件|傳回值|  
|--------|--------|---------|  
|`strtod`|溢位|\+\/\- `HUGE_VAL`|  
|`strtod`|反向溢位或沒有轉換|0|  
|`strtol`|\+ Overflow|**LONG\_MAX**|  
|`strtol`|\- Overflow|**LONG\_MIN**|  
|`strtol`|反向溢位或沒有轉換|0|  
|`_strtoi64`|\+ Overflow|**\_I64\_MAX**|  
|`_strtoi64`|\- Overflow|**\_I64\_MIN**|  
|`_strtoi64`|No conversion|0|  
|`_strtoui64`|溢位|**\_UI64\_MAX**|  
|`_strtoui64`|No conversion|0|  
  
 **\_I64\_MAX**， \_**I64\_MIN**和 **\_UI64\_MAX** 在 LIMITS.H. 定義。  
  
 `wcstod`、 `wcstol`、 `wcstoul`、 `_wcstoi64`和 `_wcstoui64` 分別為 `strtod`、 `strtol`、 `strtoul`、 `_strtoi64`和 `_strtoui64`寬字元版本；對結束轉換引數的指標對這些寬字元函式都是寬字元字串。  否則，這些寬字元函式都與相同的行為與其單一位元組字元對應。  
  
## 請參閱  
 [資料轉換](../c-runtime-library/data-conversion.md)   
 [地區設定](../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [浮點支援](../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)