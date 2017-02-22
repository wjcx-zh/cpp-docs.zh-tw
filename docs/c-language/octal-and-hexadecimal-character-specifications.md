---
title: "八進位和十六進位字元規格 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "十六進位字元"
  - "八進位字元"
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 八進位和十六進位字元規格
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\\** *ooo* 序列表示，您可以將 ASCII 字元集中的任何字元指定為三位數的八進位字元碼。  八進位整數的數值會指定所需字元或寬字元的值。  
  
 同樣地，**\\x***hhh* 序列可讓您將任何 ASCII 字元指定為十六進位字元碼。  例如，您可以用一般 C 逸出序列 \(**\\b**\) 指定 ASCII 退格鍵，或者將它編碼為 **\\010** \(八進位\) 或 **\\x008** \(十六位元\)。  
  
 在八進位逸出序列中只能使用數字 0 到 7。  八進位逸出序列的長度絕不可超過三位數，而且會在遇到不是八進位數字的第一個字元時結束。  雖然您不需要這三個位數全部使用，但是必須至少使用一個。  例如，ASCII 退格鍵的八進位表示是 **\\10**，字母 A 則是 **\\101**，如 ASCII 圖表中所示。  
  
 同樣地，您必須至少針對十六進位逸出序列使用一個位數，不過可以省略第二和第三位數。  因此，您可以將十六進位逸出序列的退格鍵字元指定為 **\\x8**、**\\x08** 或 **\\x008**。  
  
 若是字元常數，八進位或十六進位逸出序列的值必須在 **unsigned char** 類型的可顯示值範圍內，若是寬字元常數，則必須在 `wchar_t` 類型的可顯示值範圍內。  如需寬字元常數的詳細資訊，請參閱[多位元組和寬字元](../c-language/multibyte-and-wide-characters.md)。  
  
 不同於八進位逸出常數，逸出序列中的十六進位數字沒有數目上的限制。  十六進位逸出序列會在遇到不是十六進位數字的第一個字元時結束。  由於十六進位數字包含字母 **a** 到 **f**，因此務必確定逸出序列會在預期的位數結束。  為了避免混淆，您可以將八進位或十六進位字元定義放在巨集定義中：  
  
```  
#define Bell '\x07'  
```  
  
 對於十六進位值，您可以中斷字串以便清楚顯示正確的值：  
  
```  
"\xabc"    /* one character  */  
"\xab" "c" /* two characters */  
```  
  
## 請參閱  
 [C 字元常數](../c-language/c-character-constants.md)