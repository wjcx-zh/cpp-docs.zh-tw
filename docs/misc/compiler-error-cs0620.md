---
title: "編譯器錯誤 CS0620 | Microsoft Docs"
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
  - "CS0620"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0620"
ms.assetid: cadd7156-0c3c-460b-844b-c9bbfb8f62df
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0620
索引子不能有 void 的類型  
  
 [indexer](../Topic/Indexers%20\(C%23%20Programming%20Guide\).md) 的傳回類型不能是 `void`。 索引子必須傳回值。  
  
 下列範例會產生 CS0620：  
  
```  
// CS0620.cs class MyClass { public static void Main() { MyClass test = new MyClass(); System.Console.WriteLine(test[2]); } void this [int intI]   // CS0620, return type cannot be void { get { // will need to return some value } } }  
```  
  
## 請參閱  
 [void](../Topic/void%20\(C%23%20Reference\).md)