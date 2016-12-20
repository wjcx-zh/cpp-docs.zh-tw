---
title: "編譯器錯誤 CS0439 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0439"
ms.assetid: 5cbac869-1b1b-45f9-98c8-38c17348035f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0439
外部別名宣告必須位於命名空間中所有其他定義的元素之前  
  
 在相同的命名空間中，當 `extern` 宣告出現在其他項目後面時，例如 `using` 宣告，就會發生這個錯誤。`extern` 宣告必須位在所有其他命名空間項目之前。  
  
## 範例  
 下列範例會產生 CS0439：  
  
```  
// CS0439.cs using System; extern alias MyType;   // CS0439 // To resolve the error, make the extern alias the first line in the file. public class Test { public static void Main() { } }  
```