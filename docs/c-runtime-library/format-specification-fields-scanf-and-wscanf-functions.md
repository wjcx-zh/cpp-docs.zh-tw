---
title: "格式規格欄位：scanf 和 wscanf 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wscanf"
  - "scanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "寬度, scanf 函式的規格"
  - "scanf 格式規格"
  - "scanf 寬度規格"
  - "scanf 類型欄位字元"
  - "類型欄位, scanf 函式"
  - "scanf 函式的格式規格欄位"
  - "類型欄位"
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 格式規格欄位：scanf 和 wscanf 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此資訊會套用至整個 `scanf` 函式家族，包括安全版本並描述用於的符號呼叫 `scanf` 函式如何剖析輸入資料流，例如 `scanf`的輸入資料流 `stdin` ，插入至程式變數的值。  
  
 格式規格都採用下列格式：  
  
 `%`\[`*`\] \[[寬度](../c-runtime-library/scanf-width-specification.md)\] \[{}[h&#124;左&#124;ll&#124;I64&#124;L](../c-runtime-library/scanf-width-specification.md)、[型別](../c-runtime-library/scanf-type-field-characters.md)  
  
 `format` 引數指定輸入的解譯，而且可能包含下列一或多項動作:  
  
-   空白字元:空白 \("\);選項 \(「\\ t」\);或新行字元 \(「\\ n」\)。  空白字元導致 `scanf` 讀取，但不是儲存，在輸入中的所有連續空白字元至下一個非空白字元。  在格式的空白字元符合任何空白字元的數字 \(包含 0\) 和組合在輸入的。  
  
-   非空白字元，除了百分比符號 \(`%`\)。  非空白字元因為 `scanf` 讀取，而非存放，比對非空白字元。  如果在輸入資料流的下一個字元不相符， `scanf` 終止。  
  
-   格式規格，引入百分比符號 \(`%`\)。  格式的規格會造成 `scanf` 讀取和呈現在輸入的字元序列化為指定型別的值。  值會指派給在引數清單中的引數。  
  
 格式由左至右讀取。  字元外部格式規格必須符合字元序列在輸入資料流的;在輸入資料流的比對字元掃描，但不會儲存。  如果在輸入資料流的字元衝突格式規格， `scanf` 結束，因此，字元在輸入資料流會保留，好像沒有讀取。  
  
 當第一個格式規格時，第一個輸入欄位的值是根據規格轉換第一個 `argument`指定的位置中。  第二個格式規格在第二個 `argument`造成第二個輸入欄位轉換和儲存，等傳遞格式字串的結尾。  
  
 輸入欄位定義，當所有字元由第一個空白字元 \(空白字元、定位字元或新行字元\) 決定，或者無法根據格式規格轉換的第一個字元，或此欄位寬度 \(如果已指定\) 為止。  如果有指定之規格的引數太多，額外引數會被評估但是被忽略。  如果引數個數不足以供格式規格使用，結果是無法預期的。  
  
 格式規格的每個欄位都是單一字元或數字表示特定格式選項。  `type` 字元，出現，則最後一個任意格式欄位後，判斷輸入欄位是解譯為字元、字串或數字。  
  
 最簡單的格式規格包含百分比符號和只包含 `type` 字元 \(例如， `%s`\)。  如果百分比符號 \(`%`\) 是沒有意義為格式控制字元的字元\)，該字元和下列字元 \(由下一個百分比符號決定\) 會將字元一般序列，也就是說，必須符合輸入字元的序列。  例如，指定要輸入百分比符號字元，請使用 `%%`。  
  
 遵循百分比符號的星號 \(`*`\) 隱藏下輸入欄位的指派，解譯，當指定之型別的欄位。  欄位掃描，但不會儲存。  
  
 安全版本 \(與 `_s` 後置字元\) 函式家族 `scanf` 要求緩衝區大小參數在型別之後透過 `c`、 `C`、 `s`、 `S` 或 `[`的每一個參數。  如需 `scanf` 函式系列的安全版本的詳細資訊，請參閱 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)。  
  
## 請參閱  
 [scanf 寬度規格](../c-runtime-library/scanf-width-specification.md)   
 [scanf 類型欄位字元](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)