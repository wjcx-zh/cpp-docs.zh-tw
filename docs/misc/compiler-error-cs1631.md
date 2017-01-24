---
title: "編譯器錯誤 CS1631 | Microsoft Docs"
ms.custom: ""
ms.date: "10/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1631"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1631"
ms.assetid: bf0c5ff9-90a3-4db6-b4ee-0b93e31614e0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1631
無法在 catch 子句主體中使用 yield 產生值  
  
 catch 子句主體內不允許 yield 陳述式。 若要避免這個錯誤，請將 yield 陳述式移出 catch 子句主體外部。  
  
 下列範例會產生 CS1631：  
  
```  
// CS1631.cs using System; using System.Collections; public class C : IEnumerable { public IEnumerator GetEnumerator() { try { } catch(Exception e) { yield return this;  // CS1631 } } public static void Main() { } }  
```