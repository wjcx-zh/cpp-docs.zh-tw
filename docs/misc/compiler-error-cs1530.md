---
title: "編譯器錯誤 CS1530 | Microsoft Docs"
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
  - "CS1530"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1530"
ms.assetid: 3844b5ef-e0ec-42df-9267-72689020f128
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1530
在命名空間中定義的項目不允許關鍵字 'new'  
  
 不需要在[命名空間](../Topic/namespace%20\(C%23%20Reference\).md) 中的任何建構上指定 [new](../Topic/new%20\(C%23%20Reference\).md) 關鍵字。  
  
 下列範例會產生 CS1530：  
  
```  
// CS1530.cs namespace a { new class i   // CS1530 { } // try the following instead class ii { public static void Main() { } } }  
```