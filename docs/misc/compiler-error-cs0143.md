---
title: "編譯器錯誤 CS0143 | Microsoft Docs"
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
  - "CS0143"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0143"
ms.assetid: dfe6f6ba-dec9-49bd-9d5b-3dc4743bd940
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0143
類型 'class' 沒有已定義的建構函式  
  
 沒有適當的建構函式可用。 這適用於內建數值類型，只要將值指派給內建數值類型即可進行初始化。  
  
 下列範例會產生 CS0143：  
  
```  
// CS0143.cs class MyClass { static public void Main () { double d = new double(4.5);   // CS0143 // Try this line instead: // double d = 4.5; } }  
```