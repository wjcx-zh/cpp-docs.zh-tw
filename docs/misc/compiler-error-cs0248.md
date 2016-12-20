---
title: "編譯器錯誤 CS0248 | Microsoft Docs"
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
  - "CS0248"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0248"
ms.assetid: a7ddfd26-a836-47b8-b432-53876e06da31
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0248
無法以負值大小建立陣列  
  
 以負數指定陣列大小。 如需詳細資訊，請參閱[陣列](../Topic/Arrays%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0248：  
  
```  
// CS0248.cs class MyClass { public static void Main() { int[] myArray = new int[-3] {1,2,3};   // CS0248, pass a nonnegative number } }  
```