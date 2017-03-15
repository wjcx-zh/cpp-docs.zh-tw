---
title: "編譯器警告 (層級 1) C4178 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4178"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4178"
ms.assetid: 2c2c8f97-a5c4-47cd-8dd2-beea172613f3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4178
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

對 switch 運算式的類型而言，case 常數 'constant' 太大  
  
 `switch` 運算式中的 case 常數不符合指派給它的類型。  
  
## 範例  
  
```  
// C4178.cpp // compile with: /W1 int main() { int i;  // maximum size of unsigned long int is 4294967295 switch( i ) { case 4294967295:   // OK break; case 4294967296:   // C4178 break; } }  
```