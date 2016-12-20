---
title: "編譯器錯誤 CS0243 | Microsoft Docs"
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
  - "CS0243"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0243"
ms.assetid: 2506e4cb-dc26-46b4-a58c-ab6bf1601144
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0243
Conditional 屬性不能用在 'method' 上，因為它是一個覆寫方法  
  
 在以 [override](../Topic/override%20\(C%23%20Reference\).md) 關鍵字標記的方法上不允許 [Conditional](http://msdn.microsoft.com/zh-tw/e1c4913b-74d0-421a-8a6d-c14b3f0e68fb) 屬性。 如需詳細資訊，請參閱[了解使用 Override 和 New 關鍵字的時機](../Topic/Knowing%20When%20to%20Use%20Override%20and%20New%20Keywords%20\(C%23%20Programming%20Guide\).md)。  
  
 編譯器絕不會繫結至覆寫方法；它只能繫結至基底方法，而 Common Language Runtime 會適當地呼叫覆寫。  
  
 下列範例會產生 CS0243：  
  
```  
// CS0243.cs // compile with: /target:library public class MyClass { public virtual void M() {} } public class MyClass2 : MyClass { [System.Diagnostics.ConditionalAttribute("MySymbol")]   // CS0243 // remove Conditional attribute or remove override keyword public override void M() {} }  
```