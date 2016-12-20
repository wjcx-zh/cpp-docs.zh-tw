---
title: "編譯器錯誤 CS0205 | Microsoft Docs"
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
  - "CS0205"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0205"
ms.assetid: 616d98cf-e7a5-4f8e-93da-fcd6e1e4de35
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0205
無法呼叫抽象基底成員: 'method'  
  
 您無法呼叫 [abstract](../Topic/abstract%20\(C%23%20Reference\).md) 方法，因為它沒有方法主體。 如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../Topic/Abstract%20and%20Sealed%20Classes%20and%20Class%20Members%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0205：  
  
```  
// CS0205.cs abstract public class MyClass { abstract public void M(); } public class MyClass2 : MyClass { public override void M() { base.M();   // CS0205, delete this line } public static void Main() { } }  
```