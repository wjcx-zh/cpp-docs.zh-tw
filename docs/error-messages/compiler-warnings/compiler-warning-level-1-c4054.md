---
title: "編譯器警告 (層級 1) C4054 | Microsoft Docs"
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
  - "C4054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4054"
ms.assetid: bdd7f6d5-f6f2-44a7-a013-39f309de7a29
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversion': 從函式指標 'type1' 到資料指標 'type2'  
  
 函式指標轉型 \(可能不正確\) 成資料指標。 這在 \/Za 下是層級 1 警告，在 \/Ze 下是層級 4 警告。  
  
 下列範例會產生 C4054：  
  
```  
// C4054.c // compile with: /W1 /Za /c int (*pfunc)(); int* f() { return (int*)pfunc;   // C4054 }  
```  
  
 這在 \/Ze 下是層級 4 警告。  
  
```  
// C4054b.c // compile with: /W4 /c int (*pfunc)(); int* f() { return (int*)pfunc;   // C4054 }  
```