---
title: "編譯器錯誤 CS0692 | Microsoft Docs"
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
  - "CS0692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0692"
ms.assetid: d2fd650b-1f84-44b1-8c7e-471cad92a85e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0692
類型參數 'identifier' 重複  
  
 在類型參數清單中，相同的名稱只能使用一次。 重新命名或移除重複的類型參數。  
  
## 範例  
 下列範例會產生 CS0692：  
  
```  
// CS0692.cs // compile with: /target:library class C <T, A, T>   // CS0692 { } class D <T, T>   // CS0692 { }  
```