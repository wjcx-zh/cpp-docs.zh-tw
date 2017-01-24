---
title: "編譯器錯誤 CS1511 | Microsoft Docs"
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
  - "CS1511"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1511"
ms.assetid: c04b5268-5bc3-41db-af6b-463ab1d802b4
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1511
關鍵字 'base' 在靜態方法中無效  
  
 [base](../Topic/base%20\(C%23%20Reference\).md) 關鍵字已用於[靜態](../Topic/static%20\(C%23%20Reference\).md)方法中。 只能在執行個體建構函式、執行個體方法或執行個體存取子中呼叫 `base`。  
  
## 範例  
 下列範例會產生 CS1511。  
  
```  
// CS1511.cs // compile with: /target:library public class A { public int j = 0; } class C : A { public void Method() { base.j = 3;   // base allowed here } public static int StaticMethod() { base.j = 3;   // CS1511 return 1; } }  
```