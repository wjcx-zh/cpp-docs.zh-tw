---
title: "C 字串常值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "常值字串, C"
  - "字串常值, 語法"
  - "字串 [C++], 字串常值"
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 字串常值
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「字串常值」是以雙引號 \(**" "**\) 括住、來自來源字元集的一連串字元。  字串常值用於表示代表一連串字元，結合在一起會構成 null 結束字串。  寬字串常值的前面一律要加上字母 **L**。  
  
## 語法  
 *string\-literal*：  
 **"** *s\-char\-sequence*  opt               **"**  
  
 **L"** *s\-char\-sequence*  opt               **"**  
  
 *s\-char\-sequence*：  
 *s\-char*  
  
 *s\-char\-sequence s\-char*  
  
 *s\-char*：  
 來源字元集的所有成員，但不包括雙引號 \("\)、反斜線 \(\\\) 或新行字元  
  
 *escape\-sequence*  
  
 下列範例是簡單的字串常值：  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 [逸出序列](../c-language/escape-sequences.md)表中列出的所有逸出程式碼都是有效的字串常值。  若要在字串常值中表示雙引號，請使用逸出序列 **\\"**。  單引號 \(**'**\) 可以不使用逸出序列表示。  反斜線 \(**\\**\) 出現在字串內時，後面必須接著第二條反斜線 \(**\\\\**\)。  反斜線出現在行尾時，一律解譯為行接續字元。  
  
## 請參閱  
 [C 的元素](../c-language/elements-of-c.md)