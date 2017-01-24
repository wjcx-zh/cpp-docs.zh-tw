---
title: "編譯器錯誤 CS1626 | Microsoft Docs"
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
  - "CS1626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1626"
ms.assetid: 3ba03383-eb24-4fd8-bf40-8b0f7d6baf0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1626
在具有 catch 子句的 try 區塊主體中不可使用 yield 產生值  
  
 如果有與 try 區塊相關聯的 catch 子句，則 try 區塊中不允許 yield 陳述式。 若要避免這個錯誤，請將 yield 陳述式移出 catch 子句。  
  
 下列範例會產生 CS1626：  
  
```  
// CS1626.cs using System.Collections; class C : IEnumerable { public IEnumerator GetEnumerator() { try { yield return this;  // CS1626 } catch { } } } public class CMain { public static void Main() { } }  
  
```