---
title: "編譯器錯誤 CS0687 | Microsoft Docs"
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
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0687
命名空間別名限定詞 '::' 一定會解析為類型或命名空間，所以不能用在這裡。 請考慮用 '.' 替代。  
  
 如果您在未預期的位置使用了剖析器解譯為類型的項目，就會發生這個錯誤。 只有在使用成員存取 \(**.**\) 運算子的成員存取運算式中，類型或命名空間名稱才有效。 如果您在其他內容中使用全域範圍運算子 \(::\)，則可能會發生這種情況。  
  
## 範例  
 下列範例會產生 CS0687：  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```