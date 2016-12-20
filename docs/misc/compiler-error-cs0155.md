---
title: "編譯器錯誤 CS0155 | Microsoft Docs"
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
  - "CS0155"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0155"
ms.assetid: 6c92984a-2b10-453e-9cb7-e6a1d1b98aa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0155
類型 catch 或 throw 必須衍生自 System.Exception  
  
 嘗試將未衍生自 **System.Exception** 的資料類型傳遞至 [catch](../Topic/try-catch%20\(C%23%20Reference\).md) 區塊。 只有衍生自 **System.Exception** 的資料類型才能傳遞至 **catch** 區塊。 如需詳細資訊，請參閱[例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)和[例外狀況和例外狀況處理](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0155：  
  
```  
// CS0155.cs using System; namespace MyNamespace { public class MyClass2 // try the following line instead // public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } catch (MyClass2)   // CS0155, resolves if you derive MyClass2 from Exception { } } } }  
```