---
title: "編譯器錯誤 CS0715 | Microsoft Docs"
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
  - "CS0715"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0715"
ms.assetid: e3cd1e46-ccfa-4678-a2ed-69245f3558ba
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0715
'static class' : 靜態類別不能包含使用者定義的運算子  
  
 使用者定義的運算子會對類別的執行個體進行操作。 靜態類別無法具現化，因此無法建立執行個體讓運算子操作。 因此，靜態類別不允許使用者定義的運算子。  
  
 下列範例會產生 CS0715：  
  
```  
// CS0715.cs public static class C { public static C operator+(C c)  // CS0715 { } public static void Main() { } }  
```