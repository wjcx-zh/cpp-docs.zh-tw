---
title: "編譯器錯誤 CS0567 | Microsoft Docs"
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
  - "CS0567"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0567"
ms.assetid: 90aefbf9-d216-4eb4-96d4-44926fa23b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0567
介面無法包含運算子  
  
 [介面](../Topic/interface%20\(C%23%20Reference\).md)定義不允許運算子。  
  
 下列範例會產生 CS0567：  
  
```  
// CS0567.cs interface IA { int operator +(int aa, int bb);   // CS0567 } class Sample { public static void Main() { } }  
```