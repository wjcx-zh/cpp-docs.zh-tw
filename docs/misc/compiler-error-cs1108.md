---
title: "編譯器錯誤 CS1108 | Microsoft Docs"
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
  - "CS1108"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1108"
ms.assetid: 26e82d6a-6ebf-4beb-912e-1bcb86b668aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1108
一個參數無法擁有所有指定的修飾詞; 該參數上有太多修飾詞。  
  
 不允許特定參數修飾詞組合 \(例如 `ref` 和 `out`\)，因為它們對編譯器而言具有互斥的意義。  
  
## 範例  
 下列範例會產生 CS1108：  
  
```  
// cs1108.cs // Compile with: /target:library public class Test { // Regular Instance Method. public void TestMethod(ref out int i) {} // CS1108 }  
```