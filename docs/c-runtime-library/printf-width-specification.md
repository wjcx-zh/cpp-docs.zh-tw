---
title: "printf 寬度規格 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf 函式, 格式規格欄位"
  - "printf 函式, 寬度規格"
ms.assetid: 8b4a1b1e-bf6e-414f-a1b6-a9b6f1b6ce92
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# printf 寬度規格
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

格式規格，第二個選項是欄位寬度規格。  `width` 引數是控制字元的最小數值輸出的非負數的十進位整數。  如果字元的數量輸出值小於指定的寬度，空白將左或值相依於右邊的左邊對齊旗標 \(`-`\) 是否為，直到指定的最小寬度為止。  如果 `width` 是 0 前置詞，以前置字元零加入整數或浮點數轉換，直到最小寬度為止，除了當轉換為無限大或 NaN 時。  
  
 寬度規格會使值截斷。  如果字元的數量輸出值大於指定的寬度，或者，如果未提供 `width` ，值的所有字元輸出，依據 [精確度。](../c-runtime-library/precision-specification.md) 規格。  
  
 如果寬度規格為星號 \(`*`\)，從引數清單的 `int` 引數將提供值。  在引數清單， `width` 引數必須在正在格式化的值之前，如範例所示:  
  
 `printf("%0*f", 5, 3);  /* 00003 is output */`  
  
 遺漏或小型 `width` 值格式規格不會產生輸出值截斷。  如果轉換的結果比 `width` 值寬，欄位展開包含轉換結果。  
  
## 請參閱  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [旗標指示詞](../c-runtime-library/flag-directives.md)   
 [精確度規格](../c-runtime-library/precision-specification.md)   
 [大小規格](../c-runtime-library/size-specification.md)   
 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)