---
title: "編譯器錯誤 C2032 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2032"
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 函式不可為 struct\/union 'structorunion' 的成員  
  
 結構或等位擁有可以用於 C\+\+ 而不能用於 C 的成員函式。  若要解決這種錯誤，請編譯成 C\+\+ 程式，或移除該成員函式。  
  
 下列範例會產生 C2032：  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 可能的解決方案：  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```