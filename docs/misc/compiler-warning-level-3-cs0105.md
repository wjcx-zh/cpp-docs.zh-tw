---
title: "編譯器警告 (層級 3) CS0105 | Microsoft Docs"
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
  - "CS0105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0105"
ms.assetid: 96d1d5d7-79e9-424f-bbde-f87e88b70003
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0105
'namespace' 的 using 指示詞之前在此命名空間出現過  
  
 [namespace](../Topic/namespace%20\(C%23%20Reference\).md)，應該只宣告一次，但卻宣告了一次以上，因此請移除所有重複的命名空間宣告。  
  
 下列範例會產生 CS0105：  
  
```  
// CS0105.cs // compile with: /W:3 using System; using System;   // CS0105 public class a { public static void Main() { } }  
```