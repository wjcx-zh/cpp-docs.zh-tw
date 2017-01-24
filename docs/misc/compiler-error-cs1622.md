---
title: "編譯器錯誤 CS1622 | Microsoft Docs"
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
  - "CS1622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1622"
ms.assetid: 6b53a777-4cd8-423a-84ff-22ff588044d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1622
無法從迭代器傳回值。 請使用 yield return 陳述式傳回值，或使用 yield break 結束反覆運算。  
  
 迭代器是一個特殊函式，可透過 yield 陳述式 \(而非 return 陳述式\) 來傳回值。 如需詳細資訊，請參閱 **iterator**。  
  
 下列範例會產生 CS1622：  
  
```  
// CS1622.cs // compile with: /target:library using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { return (IEnumerator) this;  // CS1622 yield return this;   // OK } }  
```