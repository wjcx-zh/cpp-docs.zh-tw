---
title: "編譯器錯誤 CS0564 | Microsoft Docs"
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
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0564
多載移位 \(Shift\) 運算子的第一個運算元的類型必須和包含類型相同，而第二個運算元的類型必須是 int  
  
 您嘗試使用不正確類型的運算元多載移位運算子 \(\<\< 或 \>\>\)。 第一個運算元必須是類型，第二個運算元必須是 `int` 類型。  
  
 下列範例會產生 CS0564：  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```