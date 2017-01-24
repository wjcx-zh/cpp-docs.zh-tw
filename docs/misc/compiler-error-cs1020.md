---
title: "編譯器錯誤 CS1020 | Microsoft Docs"
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
  - "CS1020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1020"
ms.assetid: e8860769-a847-4248-a37b-77a59863467c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1020
必須是可多載的二元運算子  
  
 已嘗試定義[運算子多載](../Topic/Overloadable%20Operators%20\(C%23%20Programming%20Guide\).md)，但運算子並非二元運算子，後者會接受兩個參數。  
  
 下列範例會產生 CS1020：  
  
```  
// CS1020.cs public class iii { public static int operator ++(iii aa, int bb)   // CS1020, change ++ to + { return 0; } public static void Main() { } }  
```