---
title: "編譯器錯誤 CS0568 | Microsoft Docs"
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
  - "CS0568"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0568"
ms.assetid: dc9e1263-f58d-4c95-9165-27ba7757bc7b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0568
結構無法包含明確無參數的建構函式  
  
 每個[結構](../Topic/struct%20\(C%23%20Reference\).md)都已有將物件初始化為零的預設建構函式。 因此，您可以為結構建立的建構函式必須採用一或多個參數。  
  
 下列範例會產生 CS0568：  
  
```  
// CS0568.cs public struct ClassY { public int field1; public ClassY(){}   // CS0568, cannot have no param constructor // Try following instead: // public ClassY(int i) // { //    field1 = i; // } } public class ClassX { public static void Main() { } }  
```