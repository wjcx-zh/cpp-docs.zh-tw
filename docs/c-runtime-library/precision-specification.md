---
title: "精確度規格 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "c.math"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf 函式, 格式規格欄位"
ms.assetid: dc59ea4e-d23a-4f1f-9881-2c919ebefb82
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 精確度規格
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

於格式規格，第三個欄位是精確度規格。  它包括一個小數點 \(.\) 後面接著非負數十進位整數，根據轉換型別，指定字串中將輸出的字元數，小數位數的數目或有效位數。  
  
 不同於寬度規格，精確度規格可能產生截斷輸出值或捨入浮點值。  如果指定 `precision` 為 0 且要轉換的值是 0，結果是未字元輸出，如下列範例所示:  
  
 `printf( "%.0d", 0 );      /* No characters output */`  
  
 如果精確度規格為星號 \(\*\)，從引數清單的 `int` 引數將提供值。  在引數清單， `precision` 引數必須在正在格式化的值之前，如範例所示:  
  
 `printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`  
  
 當省略 `precision` 時，這個型別會決定 `precision` 的解譯或預設的精確度，如下表所示，。  
  
### 整數位數值如何影響型別  
  
|類型|意義|預設|  
|--------|--------|--------|  
|`a`, `A`|精確度指定小數點之後的位數。|預設有效位數為 6。  如果精確度為 0，不印出小數點，除非使用 `#` 旗標。|  
|`c`, `C`|這個精確度沒有作用。|列印出字元。|  
|`d`, `i`, `u`, `o`, `x`, `X`|這個精確度指定要印出的最少位數。  如果位數引數小於 `precision`，輸出值在左邊填補零。  表示數字的數目超過 `precision`時，則這些值不會被截斷。|預設有效位數為 1。|  
|`e`, `E`|精確度指定小數點之後需要印出的位數。  上次列印的數字已捨入。|預設有效位數為 6。  如果 `precision` 為 0 或句號 \(.\) 出現，而後面沒有數字，不會列印小數點。|  
|`f`|精確度數值指示小數點之後需要的位數。  如果小數點出現，在它之前至少有一個數字。  值會四捨五入成數字的適當位數。|預設有效位數為 6。  如果 `precision` 為 0 ，或是如果句號 \(.\) 出現而後面沒有數字，將不會列印小數點。|  
|`g`, `G`|這個精確度指定列印的有效位數上限。|印出六個有效位數，截斷所有後端的零。|  
|`s`, `S`|這個精確度指定要列印的最大字元數。  超過 `precision` 的字元不會列印。|列印字元直到遇到 Null 字元。|  
  
## 請參閱  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [旗標指示詞](../c-runtime-library/flag-directives.md)   
 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)   
 [大小規格](../c-runtime-library/size-specification.md)   
 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)