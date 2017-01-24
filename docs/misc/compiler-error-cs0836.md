---
title: "編譯器錯誤 CS0836 | Microsoft Docs"
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
  - "CS0836"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0836"
ms.assetid: 74a12271-1612-45aa-a398-7964e0269892
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0836
常數運算式中不可使用匿名類型。  
  
 常數運算式中只允許結合了常數運算式的具名常數、常值和數學運算式。  
  
### 更正這個錯誤  
  
1.  將匿名類型變成具名類型。  
  
## 範例  
 下例示範產生 CS0836 的一種方法：  
  
```  
// cs0836.cs using System; [AttributeUsage(AttributeTargets.Class, AllowMultiple = true, Inherited = false)] public class A : Attribute { public A(object obj) { } } [A(new { })] // CS0836 public class B { } public class Test { public static int Main() { return 0; } }  
```