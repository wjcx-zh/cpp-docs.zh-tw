---
title: "編譯器錯誤 CS0157 | Microsoft Docs"
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
  - "CS0157"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0157"
ms.assetid: a5d9d506-81f8-47dd-85b6-85f8170bcbef
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0157
控制項不可脫離 finally 子句的主體  
  
 必須執行 [finally](../Topic/try-catch-finally%20\(C%23%20Reference\).md) 子句中的所有陳述式。 如需詳細資訊，請參閱[例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)和[例外狀況和例外狀況處理](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0157：  
  
```  
// CS0157.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } finally { return;   // CS0157, cannot leave finally clause } } } }  
```