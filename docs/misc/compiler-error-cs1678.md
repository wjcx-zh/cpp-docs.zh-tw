---
title: "編譯器錯誤 CS1678 | Microsoft Docs"
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
  - "CS1678"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1678"
ms.assetid: 2be8aa17-81e2-47b0-b239-e41e0c5c0d97
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1678
參數 'number' 宣告為類型 'type1'，但應該是 'type2'  
  
 當匿名方法中的參數類型和轉換方法的委派宣告不同時，就會發生這個錯誤。  
  
 下列範例會產生 CS1678：  
  
```  
// CS1678 delegate void D(int i); class Errors { static void Main() { D d = delegate(string s) { };   // CS1678 // To resolve, use the following line instead: // D d = delegate(int s) { }; } }  
```