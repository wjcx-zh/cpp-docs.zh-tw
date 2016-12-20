---
title: "編譯器錯誤 CS0150 | Microsoft Docs"
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
  - "CS0150"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0150"
ms.assetid: 1fd08ca5-e1a9-42f5-93de-2916a3bdcad1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0150
必須是常數值  
  
 找到必須有常數的變數。 如需詳細資訊，請參閱[switch](../Topic/switch%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0150：  
  
```  
// CS0150.cs namespace MyNamespace { public class MyClass { public static void Main() { int i = 0; int j = 0; switch(i) { case j:   // CS0150, j is a variable int, not a constant int // try the following line instead // case 1: } } } }  
```  
  
 以變數值指定並以陣列初始設定式初始化陣列大小時，也會產生這個錯誤。 若要移除此錯誤，請以一或多個個別陳述式初始化陣列。  
  
```  
// CS0150.cs namespace MyNamespace { public class MyClass { public static void Main() { int size = 2; double[] nums = new double[size] { 46.9, 89.4 }; //CS0150 // Try the following lines instead // double[] nums = new double[size]; // nums[0] = 46.9; // nums[1] = 89.4; } } }  
  
```