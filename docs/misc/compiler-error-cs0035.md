---
title: "編譯器錯誤 CS0035 | Microsoft Docs"
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
  - "CS0035"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0035"
ms.assetid: a622113e-98a4-4583-992c-1fb55139320a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0035
運算子 'operator' 用在類型 'type' 的運算元上時其意義會模稜兩可  
  
 編譯器有多個可用的轉換，而且不知道套用運算子之前要選擇哪個轉換。 如需詳細資訊，請參閱 [樣板化的使用者定義轉換](../misc/templated-user-defined-conversions.md) 與 [轉換運算子](../Topic/Conversion%20Operators%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0035：  
  
```  
// CS0035.cs class MyClass { private int i; public MyClass(int i) { this.i = i; } public static implicit operator double(MyClass x) { return (double) x.i; } public static implicit operator decimal(MyClass x) { return (decimal) x.i; } } class MyClass2 { static void Main() { MyClass x = new MyClass(7); object o = - x;   // CS0035 // try a cast: // object o = - (double)x; } }  
  
```