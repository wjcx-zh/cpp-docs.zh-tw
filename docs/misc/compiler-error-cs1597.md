---
title: "編譯器錯誤 CS1597 | Microsoft Docs"
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
  - "CS1597"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1597"
ms.assetid: 735e7cde-38de-4e15-96cc-ce75ffe34ff2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1597
方法或存取子區塊後的分號無效  
  
 不需要 \(或不允許\) 用分號結束方法或存取子區塊。  
  
 下例會產生 CS1597：  
  
```  
// CS1597.cs class TestClass { public static void Main() { };   // CS1597, remove semicolon }  
```