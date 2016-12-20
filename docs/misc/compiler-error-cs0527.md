---
title: "編譯器錯誤 CS0527 | Microsoft Docs"
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
  - "CS0527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0527"
ms.assetid: 1acd244b-c55b-424f-b038-a130d65b8685
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0527
介面清單中的類型 'type' 不是介面  
  
 [結構](../Topic/struct%20\(C%23%20Reference\).md)或[介面](../Topic/interface%20\(C%23%20Reference\).md)可能繼承自另一個介面，而不是繼承自任何其他類型。  
  
 下列範例會產生 CS0527：  
  
```  
// CS0527.cs // compile with: /target:library public struct clx : int {}   // CS0527 int not an interface  
```