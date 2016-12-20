---
title: "編譯器錯誤 CS0156 | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0156
最內層 catch 子句中巢狀 finally 子句不允許沒有引數的 throw 陳述式  
  
 沒有任何參數的 [throw](../Topic/throw%20\(C%23%20Reference\).md) 陳述式只會出現在不接受任何參數的 **catch** 子句中。  
  
 如需詳細資訊，請參閱[例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)和[例外狀況和例外狀況處理](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0156：  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```