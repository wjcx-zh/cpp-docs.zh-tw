---
title: "編譯器錯誤 CS1689 | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1689
屬性 'Attribute Name' 只在方法或屬性類別上有效  
  
 這個錯誤只會發生在 **ConditionalAttribute** 屬性。 如此訊息所述，這個屬性只能用於方法或屬性類別上。 例如，嘗試將這個屬性套用至類別會產生這個錯誤。  
  
## 範例  
 下列範例會產生 CS1689。  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```