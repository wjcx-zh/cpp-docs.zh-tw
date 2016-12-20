---
title: "旗標指示詞 | Microsoft Docs"
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
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "旗標指示詞 printf 函式"
  - "printf 函式的格式規格欄位"
  - "print 旗標指示詞"
  - "printf 函式, 格式規格欄位"
ms.assetid: b00cbdc9-1e5c-4b30-9f56-c1ef8d383767
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 旗標指示詞
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

格式規格，第一個選項欄位是 `flags`。  旗標是指示詞指定輸出標記、空白、前置字元零、小數點和八進位和十六進位前置對齊和輸出的字元。  格式指定名稱可出現多個旗標指示詞，且旗標能以任何順序排列。  
  
### 旗標字元  
  
|旗標|意義|預設|  
|--------|--------|--------|  
|`–`|靠左對齊特定欄位寬度內的結果。|靠右對齊|  
|`+`|使用一個標記 \(\+ 或 \-\) 給輸出值的前置字元，如果它是一個帶正負號的型別。|標記為的不帶正負號的值只會出現 \(\-\)。|  
|`0`|如果 `width` 是 `0`的前置詞，以前置字元零將，直到最小寬度為止。  如果 `0` 和 `–` 時，會忽略 `0` 。  如果指定 `0` ，因為整數格式 \(`i`、 `u`、 `x`、 `X`、 `o`， `d`\) 和精確度規格也是目前 \(例如 `%04.d`\)， `0` 會被忽略。|無填補。|  
|blank \(' '\)|如果其簽署和正值，請使用空白寫入輸出值的前面。  如果空白，將和 \+ 旗標時，空白都會被忽略。|而非保持空白隨即出現。|  
|`#`|當它使用了與 `o`、 `x`或 `X` 格式時， `#` 旗標使用 0， 0x 或 0X，分別，給任何非零的輸出值的前面。|而非保持空白隨即出現。|  
||當它使用了與 `e`、 `E`、 `f`、 `a` 或 `A` 格式時， `#` 旗標強制輸出值包含小數點。|只有數字後面，小數點隨即出現。|  
||當它使用了與 `g` 或 `G` 格式，則 `#` 旗標可能包含小數點的輸出值並防止結尾零截斷。<br /><br /> 忽略當搭配 `c`、 `d`、 `i`、 `u`或 `s`。|只有數字後面，小數點隨即出現。  結尾的零截斷。|  
  
## 請參閱  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [printf 寬度規格](../c-runtime-library/printf-width-specification.md)   
 [精確度規格](../c-runtime-library/precision-specification.md)   
 [大小規格](../c-runtime-library/size-specification.md)   
 [printf 類型欄位字元](../c-runtime-library/printf-type-field-characters.md)