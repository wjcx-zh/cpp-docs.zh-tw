---
title: "編譯器錯誤 CS1625 | Microsoft Docs"
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
  - "CS1625"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1625"
ms.assetid: 0b25b7f9-a585-49b0-9ee6-4384e87fcea6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1625
finally 子句的主體中不可使用 yield  
  
 finally 子句的主體中不允許 yield 陳述式。 若要避免這個錯誤，請將 yield 陳述式移出 finally 子句。  
  
 下列範例會產生 CS1625：  
  
```  
// CS1625.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { try { } finally { yield return this;  // CS1625 } } } public class CMain { public static void Main() { } }  
  
```