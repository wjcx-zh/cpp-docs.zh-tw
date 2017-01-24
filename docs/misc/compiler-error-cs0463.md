---
title: "編譯器錯誤 CS0463 | Microsoft Docs"
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
  - "CS0463"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0463"
ms.assetid: 0cb4be4e-86ea-4ade-8817-b17d4cacd4d5
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0463
十進位常數運算式評估失敗，錯誤: 'error'  
  
 在編譯時期，如果常數十進位運算式溢位，則會發生這個錯誤。  
  
 您通常會在執行階段收到溢位錯誤。 在此情況下，您已定義常數運算式，因此編譯器可以評估結果，並且知道會發生溢位。  
  
## 範例  
 下列程式碼會產生錯誤 CS0463。  
  
```  
// CS0463.cs using System; class MyClass { public static void Main() { const decimal myDec = 79000000000000000000000000000.0m + 79000000000000000000000000000.0m; // CS0463 Console.WriteLine(myDec.ToString()); } }  
```