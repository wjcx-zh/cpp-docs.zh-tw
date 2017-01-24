---
title: "編譯器警告 (層級 1) C4822 | Microsoft Docs"
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
  - "C4822"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4822"
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4822
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member: 區域類別成員函式沒有主體  
  
 區域類別成員函式已宣告但未定義於類別中。 若要使用區域類別成員函式，您必須在類別中定義它。 您不能在類別中宣告它，但在類別外定義它。  
  
 區域類別成員函式的任何類別外定義會發生錯誤。  
  
 下列範例會產生 C4822：  
  
```  
// C4822.cpp // compile with: /W1 int main() { struct C { void func1(int);   // C4822 // try the following line instead // void func1(int){} }; }  
```