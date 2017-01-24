---
title: "編譯器警告 (層級 4) C4130 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4130"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4130"
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4130
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator': 以字串常數的位址進行邏輯運算  
  
 搭配使用運算子與字串常值的位址會產生非預期的程式碼。  
  
 下列範例會產生 C4130：  
  
```  
// C4130.cpp // compile with: /W4 int main() { char *pc; pc = "Hello"; if (pc == "Hello") // C4130 { } }  
```  
  
 **if** 陳述式比較指標 `pc` 中所儲存的值與字串 "Hello" 的位址，而這個位址是在每次字串出現在程式碼時個別配置。**if** 陳述式不會比較 `pc` 所指向的字串與字串 "Hello"。  
  
 若要比較字串，請使用 `strcmp` 函式。