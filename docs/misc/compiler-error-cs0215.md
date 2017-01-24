---
title: "編譯器錯誤 CS0215 | Microsoft Docs"
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
  - "CS0215"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0215"
ms.assetid: 2060440d-be22-4c10-8b26-43b08b615447
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0215
運算子 True 或 False 的傳回類型必須為 bool  
  
 使用者定義的 [true](../Topic/true%20\(C%23%20Reference\).md) 和 [false](../Topic/false%20\(C%23%20Reference\).md) 運算子必須具有傳回類型 [bool](../Topic/bool%20\(C%23%20Reference\).md)。 如需詳細資訊，請參閱[多載運算子](../Topic/Overloadable%20Operators%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0215：  
  
```  
// CS0215.cs class MyClass { public static int operator true (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator true (MyClass MyInt) { return true; } public static int operator false (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator false (MyClass MyInt) { return true; } public static void Main() { } }  
```