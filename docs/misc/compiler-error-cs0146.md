---
title: "編譯器錯誤 CS0146 | Microsoft Docs"
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
  - "CS0146"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0146"
ms.assetid: 2be796e5-da2c-4939-af12-3145cd1828c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0146
循環基底類別相依包括 'class1' 和 'class2'  
  
 類別的繼承清單包含它本身的直接或間接參考。 類別不能自己繼承自己。 如需詳細資訊，請參閱[繼承](../Topic/Inheritance%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0146：  
  
```  
// CS0146.cs namespace MyNamespace { public interface InterfaceA { } public class MyClass : InterfaceA, MyClass2 { public void Main() { } } public class MyClass2 : MyClass   // CS0146 { } }  
```