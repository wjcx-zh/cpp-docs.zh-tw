---
title: "編譯器錯誤 C2548 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2548"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2548"
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2548
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::member' : 遺漏參數 parameter 的預設參數  
  
 預設的參數清單遺漏了一個參數。  如果您在參數清單上任一處提供了一個預設參數，則您必須對之後的所有參數定義預設參數。  
  
## 範例  
 下列範例會產生 C2548：  
  
```  
// C2548.cpp  
// compile with: /c  
void func( int = 1, int, int = 3);  // C2548  
  
// OK  
void func2( int, int, int = 3);  
void func3( int, int = 2, int = 3);  
```