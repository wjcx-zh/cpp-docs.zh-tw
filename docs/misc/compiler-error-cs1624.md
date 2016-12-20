---
title: "編譯器錯誤 CS1624 | Microsoft Docs"
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
  - "CS1624"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1624"
ms.assetid: af7d049d-27e2-4ce1-973c-5c2cb3e56a63
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1624
'accessor' 的主體不可是 Iterator 區塊，因為 'type' 不是 Iterator 介面類型。  
  
 如果使用了迭代器存取子，但傳回的類型不是迭代器介面類型其中之一，就會發生這個錯誤：<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、<xref:System.Collections.Generic.IEnumerator%601>。 若要避免這個錯誤，傳回類型請使用其中一個迭代器介面類型。  
  
## 範例  
 下列範例會產生 CS1624：  
  
```  
// CS1624.cs using System; using System.Collections; class C { public int Iterator // Try this instead: // public IEnumerable Iterator { get  // CS1624 { yield return 1; } } }  
```