---
title: "編譯器錯誤 CS0231 | Microsoft Docs"
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
  - "CS0231"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0231"
ms.assetid: e5e6a8e1-6c9f-4a88-8935-7bedfba88f8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0231
params 參數必須是型式參數清單中的最後一個參數。  
  
 [params](../Topic/params%20\(C%23%20Reference\).md) 參數支援數目不定的引數，且必須在所有其他參數之後。 如需詳細資訊，請參閱[方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0231：  
  
```  
// CS0231.cs class Test { public void TestMethod(params int[] p, int i) {} // CS0231 // To resolve the error, use the following line instead: // public void TestMethod(int i, params int[] p) {} static void Main() { } }  
```