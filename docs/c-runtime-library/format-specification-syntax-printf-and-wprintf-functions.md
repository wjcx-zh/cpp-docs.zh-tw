---
title: "格式規格語法：printf 和 wprintf 函式 | Microsoft Docs"
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
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "旗標指示詞 printf 函式"
  - "printf 函式的格式規格欄位"
  - "整數位數欄位"
  - "print 旗標指示詞"
  - "printf 函式, 格式規格欄位"
  - "printf 函式, 精確度"
  - "類型欄位"
  - "類型欄位, printf 函式"
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 格式規格語法：printf 和 wprintf 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述對於 `printf`、`wprintf` 和相關函式的格式字串引數之語法。  這些函式有更安全的版本可用；如需詳細資訊，請參閱 [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  如需個別函式的資訊，請參閱這些特定函式的文件。  如需這些函式的清單，請參閱[資料流 I\/O](../c-runtime-library/stream-i-o.md)。  
  
 格式規格，其中包含選擇性及必要的欄位，具有下列格式：  
  
 `%`\[[旗標](../c-runtime-library/flag-directives.md)\] \[[寬度](../c-runtime-library/printf-width-specification.md)\] \[**.**[精準度](../c-runtime-library/precision-specification.md)\] \[{`h` &#124; `l` &#124; `ll` &#124; `w` &#124; `I` &#124; `I32` &#124; `I64`}\] [類型](../c-runtime-library/printf-type-field-characters.md)  
  
 每個格式規格的欄位都是字元，或是表示特定格式選項或轉換規範的數字。  必要的 `type` 字元會指定要套用至引數的轉換種類。  選擇性的 `flags`、`width` 和 `precision` 欄位控制其他格式層面。  一個基本格式規格只能包含百分比符號和一個 `type` 字元，例如指定字串轉換的 `%s`。  在這些函式的安全版本中，如果百分比符號後接著的字元不代表任何格式欄位，則會叫用無效參數處理常式。  如需詳細資訊，請參閱[參數驗證](../c-runtime-library/parameter-validation.md)。  在非安全版本中，會將此字元原封不動地複製到輸出。  若要列印百分比符號字元，請使用 `%%`。  
  
 格式規格欄位會控制引數轉換和格式化的下列層面：  
  
 `type`  
 必要的轉換規範字元，決定是否將相關聯的 `argument` 解譯為字元、字串、整數或浮點數。  如需詳細資訊，請參閱 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)。  
  
 `flags`  
 選擇性的字元，或是控制輸出對齊和輸出正負號、空白、前置零字元、小數點、八進位和十六進位之前置字元的字元。  如需詳細資訊，請參閱[旗標指示詞](../c-runtime-library/flag-directives.md)。  格式規格中可出現多個旗標，且旗標能以任何順序排列。  
  
 `width`  
 選擇性的十進位數字，該數字會指定輸出的字元最小數目。  如需詳細資訊，請參閱 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)。  
  
 `precision`  
 選擇性的十進位數字，對於字串指定列印的字元數最大數目，對於浮點數值指定有效位數的數目或小數點字元後的數字位數，或是對於整數值指定列印的數字位數最小數目。  如需詳細資訊，請參閱[精確度規格](../c-runtime-library/precision-specification.md)中的〈精確度值如何影響類型〉。  
  
 `h` &#124; `l` &#124; `ll` &#124; `w` &#124; `I` &#124; `I32` &#124; `I64`  
 對 `type` 的選擇性前置詞，會指定對應的引數大小。  如需詳細資訊，請參閱[大小規格](../c-runtime-library/size-specification.md)中的〈大小前置詞〉。  
  
> [!IMPORTANT]
>  請確定格式規格字串不是使用者定義的。  例如，考慮一個請使用者輸入名稱的程式，且該程式將輸入儲存在名為 `name` 的字串變數。  若要印出 `name`，請勿採用此做法：  
>   
>  `printf( name ); /* Danger!  If name contains "%s", program will crash */`  
>   
>  相反地，請這樣做：  
>   
>  `printf( "%s", name );`  
  
## 請參閱  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [printf\_p 位置參數](../c-runtime-library/printf-p-positional-parameters.md)   
 [旗標指示詞](../c-runtime-library/flag-directives.md)   
 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)   
 [精確度規格](../c-runtime-library/precision-specification.md)   
 [大小規格](../c-runtime-library/size-specification.md)   
 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)