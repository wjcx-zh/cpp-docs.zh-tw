---
title: "編譯器錯誤 CS0541 | Microsoft Docs"
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
  - "CS0541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0541"
ms.assetid: ed812c07-24f7-43c6-9a44-553f27f6249d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0541
'declaration': 明確介面宣告只能在類別或結構中宣告  
  
 在[類別](../Topic/class%20\(C%23%20Reference\).md)或[結構](../Topic/struct%20\(C%23%20Reference\).md)之外發現明確的[介面](../Topic/interface%20\(C%23%20Reference\).md)宣告。  
  
 下列範例會產生 CS0541：  
  
```  
// CS0541.cs namespace x { interface IFace { void F(); } interface IFace2 : IFace { void IFace.F();   // CS0541 } }  
```