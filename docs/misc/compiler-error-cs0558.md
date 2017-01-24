---
title: "編譯器錯誤 CS0558 | Microsoft Docs"
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
  - "CS0558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0558"
ms.assetid: af63b9ba-2790-4362-a49d-b69a5292a555
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0558
使用者定義的運算子 'operator' 必須宣告為 static 和 public  
  
 使用者定義的運算子都必須指定 **static** 和 **public** 存取[修飾詞](../Topic/Modifiers%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS0558：  
  
```  
// CS0558.cs namespace x { public class ii { public class iii { static implicit operator int(iii aa)   // CS0558, add public { return 0; } } public static void Main() { } } }  
```