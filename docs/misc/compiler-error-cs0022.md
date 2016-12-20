---
title: "編譯器錯誤 CS0022 | Microsoft Docs"
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
  - "CS0022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0022"
ms.assetid: 531c3ed2-0d75-4046-8d57-89f79381af8e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0022
\[\] 內的索引數目錯誤; 必須是 'number'  
  
 陣列存取作業在方括弧內指定的維度數目不正確。 如需詳細資訊，請參閱[陣列](../Topic/Arrays%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0022：  
  
```  
// CS0022.cs public class MyClass { public static void Main() { int[] a = new int[10]; a[0] = 0;     // single-dimension array a[0,1] = 9;   // CS0022, the array does not have two dimensions } }  
```