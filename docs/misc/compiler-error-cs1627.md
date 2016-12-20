---
title: "編譯器錯誤 CS1627 | Microsoft Docs"
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
  - "CS1627"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1627"
ms.assetid: 58dd6e22-e9ed-4e5c-ae04-ce255f07064e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1627
yield return 之後應接著運算式  
  
 如果使用 `yield` 但沒有運算式，就會發生這個錯誤。 若要避免這個錯誤，請在陳述式中插入適當的運算式。  
  
 下列範例會產生 CS1627：  
  
```  
// CS1627.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { yield return;   // CS1627 // To resolve, add the following line: // yield return 0; } } public class CMain { public static void Main() { } }  
```