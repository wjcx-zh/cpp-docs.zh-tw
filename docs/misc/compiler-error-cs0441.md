---
title: "編譯器錯誤 CS0441 | Microsoft Docs"
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
  - "CS0441"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0441"
ms.assetid: 3f07500a-d479-424c-a0f4-c219be1b5a45
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0441
'class': 類別不可同時為 static 和 sealed  
  
 當您宣告同時為 static 和 sealed 的類別時，會發生這個錯誤。 static 類別原本就進行密封，因此不需要 sealed 修飾詞。 若要解決，請僅使用一個修飾詞。  
  
 下列範例會產生 CS0441：  
  
```  
// CS0441.cs sealed static class MyClass { }   // CS0441  
```