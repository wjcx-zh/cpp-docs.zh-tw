---
title: "編譯器錯誤 CS1528 | Microsoft Docs"
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
  - "CS1528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1528"
ms.assetid: 38aabc5c-b32f-4bea-a585-c4212f42751d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1528
必須是 ; 或 \= \(無法在宣告中指定建構函式引數\)  
  
 類別參考的格式，就像建立類別的物件一樣。 例如，嘗試將變數傳遞至建構函式。 使用 [new](../Topic/new%20\(C%23%20Reference\).md) 運算子建立類別的物件。  
  
 下列範例會產生 CS1528：  
  
```  
// CS1528.cs using System; public class B { public B(int i) { _i = i; } public void PrintB() { Console.WriteLine(_i); } private int _i; } public class mine { public static void Main() { B b(3);   // CS1528, reference is not an object // try one of the following // B b; // or // B bb = new B(3); // bb.PrintB(); } }  
```