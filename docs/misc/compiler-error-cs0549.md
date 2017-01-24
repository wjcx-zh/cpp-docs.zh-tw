---
title: "編譯器錯誤 CS0549 | Microsoft Docs"
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
  - "CS0549"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0549"
ms.assetid: ae965019-9dee-4f28-9e9a-6f379bd0d757
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0549
'function' 是密封類別 'class' 的新虛擬成員  
  
 [密封](../Topic/sealed%20\(C%23%20Reference\).md) [類別](../Topic/class%20\(C%23%20Reference\).md)不能當做基底類別使用。  因此，虛擬方法在密封類別中毫無作用。  
  
 下列範例會產生 CS0549：  
  
```  
// CS0549.cs // compile with: /target:library sealed public class MyClass { virtual public void TestMethod() {}   // CS0549 public void TestMethod2() {}   // OK }  
```