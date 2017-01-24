---
title: "編譯器錯誤 CS0131 | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0131
指派的左方必須是變數、屬性或索引子  
  
 在指派陳述式中，右方的值已指派給左方。 左方必須是變數、屬性或索引子。  
  
 若要修正這個錯誤，請確定所有運算子都在右方，且左方為變數、屬性或索引子。 如需詳細資訊，請參閱[陳述式、運算式和運算子](../Topic/Statements,%20Expressions,%20and%20Operators%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0131。  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## 範例  
 如果您嘗試在指派運算子左方執行算術運算，也會發生這個錯誤，如下列範例所示。  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```