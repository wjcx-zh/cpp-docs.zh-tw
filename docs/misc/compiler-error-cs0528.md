---
title: "編譯器錯誤 CS0528 | Microsoft Docs"
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
  - "CS0528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0528"
ms.assetid: 8f5dde55-7e4f-4ffa-be14-0e0f3a538118
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0528
'interface' 已經列於介面清單  
  
 介面繼承清單包含重複項目。 一個[介面](../Topic/interface%20\(C%23%20Reference\).md)只能在繼承清單中指定一次。  
  
 下列範例會產生 CS0528：  
  
```  
// CS0528.cs namespace x { public interface a { } public class b : a, a   // CS0528 { public void Main() { } } }  
```