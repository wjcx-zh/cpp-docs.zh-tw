---
title: "編譯器警告 (層級 4) C4127 | Microsoft Docs"
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
  - "C4127"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4127"
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 12
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4127
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

條件運算式是常數  
  
 `if` 陳述式或 `while` 迴圈的控制運算式會評估為常數。 如果 `while` 迴圈的控制運算式由於迴圈將在中間結束而為常數，請考慮以 `for` 迴圈取代 `while` 迴圈。 您可以省略初始化、終止測試，以及造成 `for` 迴圈成為無限迴圈 \(例如 `while(1)`\) 的迴圈遞增，而且您可以從 `for` 陳述式的主體結束迴圈。  
  
 下列範例會產生 C4127：  
  
```  
// C4127.cpp // compile with: /W4 #include <stdio.h> int main() { if (1 == 1) {}   // C4127 while (1) { break; }   // C4127 // OK for ( ; ; ) { printf("test\n"); break; } }  
```