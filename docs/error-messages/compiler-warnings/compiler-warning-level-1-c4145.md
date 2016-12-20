---
title: "編譯器警告 (層級 1) C4145 | Microsoft Docs"
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
  - "C4145"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4145"
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4145
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'expression1': 關聯運算式作為 switch 運算式；可能與 '%$L' 混淆  
  
 `switch` 陳述式使用關聯運算式作為其控制運算式，因而導致 **case** 陳述式的布林值。 您是不是指 *expression2*？  
  
## 範例  
 下列範例會產生 C4145：  
  
```  
// C4145.cpp // compile with: /W1 int main() { int i = 0; switch(i == 1) {   // C4145, use i instead of i == 1 to resolve case 1: break; default: break; } }  
```