---
title: "編譯器錯誤 CS1525 | Microsoft Docs"
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
  - "CS1525"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1525"
ms.assetid: 7913f589-2f2e-40bc-a27e-0b6930336484
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1525
無效的運算式詞彙 'character'  
  
 編譯器偵測到運算式中有無效的字元。  
  
 下列範例會產生 CS1525：  
  
```  
// CS1525.cs class x { public static void Main() { int i = 0; i = i +   // OK - identifier 'c' +     // OK - character (5) +     // OK - parenthesis [ +       // CS1525, operator not a valid expression element throw +   // CS1525, keyword not allowed in expression void;     // CS1525, void not allowed in expression } }  
```  
  
 空白標籤也會產生 CS1525，如下列範例所示：  
  
```  
// CS1525b.cs using System; public class MyClass { public static void Main() { goto FoundIt; FoundIt:      // CS1525 // Uncomment the following line to resolve: // System.Console.Write("Hello"); } }  
```