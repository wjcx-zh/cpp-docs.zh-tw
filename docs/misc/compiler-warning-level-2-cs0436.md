---
title: "編譯器警告 (層級 2) CS0436 | Microsoft Docs"
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
  - "CS0436"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0436"
ms.assetid: c4135d9d-3511-4bbc-9540-48c2091f869c
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0436
'assembly' 中的類型 'type' 與 'assembly' 中匯入的類型 'type2' 相衝突。 請使用 'assembly' 中定義的類型。  
  
 原始程式檔 \(file\_2\) 中的類型與 file\_1 中匯入的類型衝突時，會發出這個警告。 編譯器會使用原始程式檔中的類型。  
  
## 範例  
  
```  
// CS0436_a.cs // compile with: /target:library public class A { public void Test() { System.Console.WriteLine("CS0436_a"); } }  
```  
  
## 範例  
 下列範例會產生 CS0436。  
  
```  
// CS0436_b.cs // compile with: /reference:CS0436_a.dll // CS0436 expected public class A { public void Test() { System.Console.WriteLine("CS0436_b"); } } public class Test { public static void Main() { A x = new A(); x.Test(); } }  
```