---
title: "編譯器錯誤 CS0111 | Microsoft Docs"
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
  - "CS0111"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0111"
ms.assetid: 87afb689-f27b-451d-84eb-d6bdf17aea41
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0111
類型 'class' 已經定義了一個具有相同參數類型名為 'member' 的成員  
  
 如果一個類別包含兩個具有相同名稱和參數類型的成員宣告，就會發生 CS0111。 如需詳細資訊，請參閱[方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0111。  
  
```  
// CS0111.cs class A { void Test() { } public static void Test(){}   // CS0111 public static void Main() {} }  
```