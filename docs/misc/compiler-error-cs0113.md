---
title: "編譯器錯誤 CS0113 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0113"
ms.assetid: 43c5c0b7-67c0-45c1-8363-21c844c094f3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0113
標記為 override 的成員 'function' 不能標記為 new 或 virtual  
  
 使用 [new](../Topic/new%20\(C%23%20Reference\).md) 和 [override](../Topic/override%20\(C%23%20Reference\).md) 關鍵字來標記方法是互斥的。  
  
 下列範例會產生 CS0113：  
  
```  
// CS0113.cs namespace MyNamespace { abstract public class MyClass { public abstract void Foo(); } public class MyClass2 : MyClass { override new public void Foo()   // CS0113, remove new keyword { } public static int Main() { return 0; } } }  
```