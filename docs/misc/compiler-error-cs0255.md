---
title: "編譯器錯誤 CS0255 | Microsoft Docs"
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
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0255
在 catch 或 finally 區塊中不可使用 stackalloc  
  
 在 [catch](../Topic/try-catch%20\(C%23%20Reference\).md) 或 [finally](../Topic/try-catch-finally%20\(C%23%20Reference\).md) 區塊中不可使用 [stackalloc](../Topic/stackalloc%20\(C%23%20Reference\).md) 關鍵字。 如需詳細資訊，請參閱[例外狀況和例外狀況處理](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0255：  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```