---
title: "編譯器錯誤 CS0217 | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0217
為了可以當成最少運算 \(Short Circuit\) 運算子使用，使用者定義的邏輯運算子 \('operator'\) 其傳回類型必須與其 2 個參數的類型相同。  
  
 如果您定義了一個使用者定義類型的運算子，然後嘗試使用該運算子作為最少運算運算子，則使用者定義運算子必須具有相同類型的參數和傳回值。 如需最少運算運算子的詳細資訊，請參閱 [&& 運算子](../Topic/&&%20Operator%20\(C%23%20Reference\).md)和 [&#124;&#124; 運算子](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0217：  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## 請參閱  
 [多載運算子](../Topic/Overloadable%20Operators%20\(C%23%20Programming%20Guide\).md)