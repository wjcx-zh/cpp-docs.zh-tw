---
title: "編譯器錯誤 CS0220 | Microsoft Docs"
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
  - "CS0220"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0220"
ms.assetid: f520bf34-bff8-4796-882b-1a9b1d5b977c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0220
檢查模式下，作業於編譯時期溢位  
  
 [checked](../Topic/checked%20\(C%23%20Reference\).md) 偵測到一項作業，這是預設值，並且會導致資料遺失。 請更正指派的輸入，或使用 [unchecked](../Topic/unchecked%20\(C%23%20Reference\).md) 來解決這個錯誤。 如需詳細資訊，請參閱[Checked 與 Unchecked](../Topic/Checked%20and%20Unchecked%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0220：  
  
```  
// CS0220.cs using System; class TestClass { const int x = 1000000; const int y = 1000000; public int MethodCh() { int z = (x * y);   // CS0220 return z; } public int MethodUnCh() { unchecked { int z = (x * y); return z; } } public static void Main() { TestClass myObject = new TestClass(); Console.WriteLine("Checked  : {0}", myObject.MethodCh()); Console.WriteLine("Unchecked: {0}", myObject.MethodUnCh()); } }  
```