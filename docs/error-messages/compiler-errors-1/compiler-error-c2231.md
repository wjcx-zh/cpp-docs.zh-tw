---
title: "編譯器錯誤 C2231 | Microsoft Docs"
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
  - "C2231"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2231"
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2231
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'.'：左運算元指向 'class\-key'，請使用 '–\>'  
  
 成員選取運算 \(.\) 的左運算元 是指標，而不是類別、結構或等位。  
  
 下列範例會產生 C2231：  
  
```  
// C2231.c struct S { int member; } s, *ps = &s; int main() { ps.member = 0;   // C2231 // OK ps->member = 0;   // crash s.member = 0; }  
```