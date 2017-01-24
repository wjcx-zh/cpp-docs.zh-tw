---
title: "編譯器錯誤 CS1900 | Microsoft Docs"
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
  - "CS1900"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1900"
ms.assetid: 08141138-bfea-4af3-a9a0-ec54cf2caa13
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1900
警告層級必須介於範圍 0 到 4 之間  
  
 [\/warn](../Topic/-warn%20\(C%23%20Compiler%20Options\).md) 編譯器選項只能採用五個可能值的其中一個 \(0、1、2、3 或 4\)。 任何其他傳遞給 **\/warn** 的值都會導致 CS1900。  
  
 下列範例會產生 CS1900：  
  
```  
// CS1900.cs // compile with: /W:5 // CS1900 expected class x { public static void Main() { } }  
```