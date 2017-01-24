---
title: "編譯器錯誤 CS0514 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0514"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0514"
ms.assetid: 74ce3010-f9e9-458c-8b68-cfb908a3e7a2
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0514
'constructor'：靜態建構函式不能有明確的 'this' 或 'base' 建構函式呼叫  
  
 不允許在靜態建構函式中呼叫 `this`，因為在建立任何類別執行個體之前會自動呼叫靜態建構函式。 此外，靜態建構函式不會被繼承，也不能直接呼叫。  
  
 如需詳細資訊，請參閱[this](../Topic/this%20\(C%23%20Reference\).md)與[base](../Topic/base%20\(C%23%20Reference\).md)。  
  
## 範例  
 下例會產生 CS0514：  
  
```  
// CS0514.cs class A { static A() : base(0) // CS0514 { } public A(object o) { } } class B { static B() : this(null) // CS0514 { } public B(object o) { } }  
```