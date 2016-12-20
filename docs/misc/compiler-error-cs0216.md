---
title: "編譯器錯誤 CS0216 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0216"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0216"
ms.assetid: afb3dd29-3eff-4b62-8267-eb726c2bcee4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0216
運算子 'operator' 的配對運算子 'missing\_operator' 也需要定義  
  
 使用者定義的 [true](../Topic/true%20\(C%23%20Reference\).md) 運算子需要使用者定義的 [false](../Topic/false%20\(C%23%20Reference\).md) 運算子，反之亦然。 如需詳細資訊，請參閱[運算子](../Topic/Operators%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0216：  
  
```  
// CS0216.cs class MyClass { public static bool operator true (MyClass MyInt)   // CS0216 { return true; } // to resolve, uncomment the following operator definition /* public static bool operator false (MyClass MyInt) { return true; } */ public static void Main() { } }  
```