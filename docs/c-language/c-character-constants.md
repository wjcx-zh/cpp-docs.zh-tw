---
title: "C 字元常數 | Microsoft Docs"
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
  - "(') 單引號"
  - "字元, 常數"
  - "常數, 字元"
  - "單引號"
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# C 字元常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「字元常數」是藉由將可表示字元集中的單一字元包含在單引號 \(**' '**\) 內所形成。  字元常數用於表示[執行字元集](../c-language/execution-character-set.md)內的字元。  
  
## 語法  
 *character\-constant*：  
 **'** *c\-char\-sequence* **'**  
  
 **L'** *c\-char\-sequence* **'**  
  
 *c\-char\-sequence*：  
 *c\-char*  
  
 *c\-char\-sequence c\-char*  
  
 *c\-char*：  
 來源字元集的所有成員，但不包括單引號 \(**'**\)、反斜線 \(**\\**\) 或新行字元  
  
 *escape\-sequence*  
  
 *escape\-sequence*：  
 *simple\-escape\-sequence*  
  
 *octal\-escape\-sequence*  
  
 *hexadecimal\-escape\-sequence*  
  
 *simple\-escape\-sequence*：下列其中一個  
 **\\a \\b \\f \\n \\r \\t \\v**  
  
 **\\' \\" \\\\ \\?**  
  
 *octal\-escape\-sequence*：  
 **\\**  *octal\-digit*  
  
 **\\**  *octal\-digit octal\-digit*  
  
 **\\**  *octal\-digit octal\-digit octal\-digit*  
  
 *hexadecimal\-escape\-sequence*：  
 **\\x**  *hexadecimal\-digit*  
  
 *hexadecimal\-escape\-sequence hexadecimal\-digit*  
  
## 請參閱  
 [C 常數](../c-language/c-constants.md)