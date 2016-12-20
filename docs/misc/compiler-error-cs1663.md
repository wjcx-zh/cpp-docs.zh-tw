---
title: "編譯器錯誤 CS1663 | Microsoft Docs"
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
  - "CS1663"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1663"
ms.assetid: 013f36ac-8925-4cee-9008-54fa7ad1324b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1663
固定大小緩衝區類型必須是下列其中一項: bool、byte、short、int、long、char、sbyte、ushort、uint、ulong、float 或 double。  
  
 固定大小緩衝區可能不是所列出類型以外的類型。 若要避免這個錯誤，請使用另一種類型，或不使用固定陣列。  
  
## 範例  
 下列範例會產生 CS1663。  
  
```  
// CS1663.cs // compile with: /unsafe /target:library unsafe struct C { fixed string ab[10];   // CS1663 }  
```