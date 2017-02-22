---
title: "編譯器錯誤 C2586 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2586"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2586"
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2586
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不正確的使用者定義轉換語法：間接取值不合法  
  
 不允許轉換運算子的間接取值 \(Indirection\)。  
  
 下列範例會產生 C2586：  
  
```  
// c2586.cpp  
// compile with: /c  
struct C {  
   * operator int();   // C2586  
   operator char();   // OK  
};  
```