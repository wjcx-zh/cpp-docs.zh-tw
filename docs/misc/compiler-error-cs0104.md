---
title: "編譯器錯誤 CS0104 | Microsoft Docs"
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
  - "CS0104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0104"
ms.assetid: 1a7e9ae8-308b-441b-ba85-fac974222875
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0104
'reference' 是 'identifier' 和 'identifier' 之間模稜兩可的參考  
  
 您的程式包含兩個命名空間的 [using](../Topic/using%20\(C%23%20Reference\).md) 指示詞，且您的程式碼參考在兩個命名空間中都出現的名稱。  
  
 下列範例會產生 CS0104：  
  
```  
// CS0104.cs using x; using y; namespace x { public class Test { } } namespace y { public class Test { } } public class a { public static void Main() { Test test = new Test();   // CS0104, is Test in x or y namespace? // try the following line instead // y.Test test = new y.Test(); } }  
```