---
title: "編譯器錯誤 C2232 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2232"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2232"
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2232
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\-\>' : 左運算元有 'class\-key' 類型，請使用 '.'  
  
 `->` 運算子左邊的運算元不是指標。 使用句號 \(.\) 類別、結構或等位的運算子。  
  
 下列範例會產生 C2232：  
  
```  
// C2232.c struct X { int member; } x, *px; int main() { x->member = 0;   // C2232, x is not a pointer px->member = 0; x.member = 0; }  
```