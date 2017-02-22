---
title: "編譯器錯誤 C2969 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2969"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2969"
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2969
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤：'symbol' : 必須是以 '}' 結尾的成員函式定義  
  
 樣板成員函式定義有不對稱的右大括弧。  
  
 下列範例會產生 C2969：  
  
```  
// C2969.cpp // compile with: /c class A { int i; public: A(int i) {} }; A anA(1); class B { A a; B() : a(anA);   // C2969 // try the following line instead // B() : a(anA) {} };  
```