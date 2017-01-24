---
title: "編譯器錯誤 CS0833 | Microsoft Docs"
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
  - "CS0833"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0833"
ms.assetid: 4ae32454-265f-47aa-bf2a-ee1d702330b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0833
匿名類型不可具有多個同名的屬性。  
  
 匿名類型就像任何類型，不能有兩個同名的屬性。  
  
### 更正這個錯誤  
  
1.  請為類型中的每個屬性指定唯一名稱。  
  
## 範例  
 下列範例會產生 CS0833：  
  
```  
// cs0833.cs using System; public class C { public static int Main() { var c = new { p1 = 1, p1 = 2 }; // CS0833 return 1; } }  
```  
  
## 請參閱  
 [匿名類型](../Topic/Anonymous%20Types%20\(C%23%20Programming%20Guide\).md)