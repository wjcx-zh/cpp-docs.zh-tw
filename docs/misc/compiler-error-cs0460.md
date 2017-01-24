---
title: "編譯器錯誤 CS0460 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0460"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0460"
ms.assetid: 98d39ded-d3f9-4520-b912-892e574c056b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0460
覆寫及明確介面實作方法的條件約束，繼承自基底方法，所以無法直接指定。  
  
 當屬於衍生類別的泛型方法覆寫基底類別中的方法時，您不能指定受覆寫的方法上的條件約束。 衍生類別中的覆寫方法會從基底類別中的方法繼承其條件約束。  
  
## 範例  
 下列範例會產生 CS0460：  
  
```  
// CS0460.cs // compile with: /target:library class BaseClass { BaseClass() { } } interface I { void F1<T>() where T : BaseClass; void F2<T>() where T : struct; void F3<T>() where T : BaseClass; } class ExpImpl : I { void I.F1<T>() where T : BaseClass {}   // CS0460 void I.F2<T>() where T : class {}  // CS0460 }  
```