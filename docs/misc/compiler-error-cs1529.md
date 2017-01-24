---
title: "編譯器錯誤 CS1529 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1529"
ms.assetid: 672a6fd1-3a1f-422c-a29f-46f196d15211
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1529
using 子句必須位於所有其他命名空間中所定義的元素之前 \(外部別名宣告除外\)  
  
 [using](../Topic/using%20\(C%23%20Reference\).md) 子句必須在命名空間中第一個出現。  
  
## 範例  
 下列範例會產生 CS1529：  
  
```  
// CS1529.cs namespace X { namespace Subspace { using Microsoft; class SomeClass { }; using Microsoft;      // CS1529, place before class definition } using System.Reflection;  // CS1529, place before namespace 'Subspace' } using System;                 // CS1529, place at the beginning of the file  
```