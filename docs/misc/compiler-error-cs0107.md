---
title: "編譯器錯誤 CS0107 | Microsoft Docs"
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
  - "CS0107"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0107"
ms.assetid: 505763c5-6d68-4c57-a8bd-7b03682da4c5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0107
有一個以上的保護修飾詞  
  
 在類別成員上只允許一個存取修飾詞 \([public](../Topic/public%20\(C%23%20Reference\).md)、[private](../Topic/private%20\(C%23%20Reference\).md)、[protected](../Topic/protected%20\(C%23%20Reference\).md) 或 [internal](../Topic/internal%20\(C%23%20Reference\).md)\)，但不包括 **internal protected**。  
  
 下列範例會產生 CS0107：  
  
```  
// CS0107.cs public class C { private internal void f()   // CS0107, delete private or internal { } public static int Main() { return 1; } }  
```