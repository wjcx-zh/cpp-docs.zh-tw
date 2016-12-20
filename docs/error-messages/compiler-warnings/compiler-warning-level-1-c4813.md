---
title: "編譯器警告 (層級 1) C4813 | Microsoft Docs"
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
  - "C4813"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4813"
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 之前一定已經宣告過區域類別的 Friend 函式  
  
 內部類別中的 Friend 函式未在外部類別中宣告。  
  
 下列範例會產生 C4813：  
  
```  
// C4813.cpp // compile with: /W1 /LD void MyClass() { // void func(); class InnerClass { friend void func();   // C4813 uncomment declaration above }; }  
```