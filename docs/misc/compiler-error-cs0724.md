---
title: "編譯器錯誤 CS0724 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0724"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0724"
ms.assetid: bcdb2017-7a43-4242-b4e2-a1ae03d6d73f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0724
不需要 CLSCompliant 屬性，因為組件並沒有 CLSCompliant 屬性  
  
 下列範例會產生 CS0724，因為 `throw` 陳述式位於 `finally` 子句區塊內。  
  
## 範例  
 下列範例會產生 CS0724。  
  
```  
// CS0724.cs using System; class X { static void Test() { try { throw new Exception(); } catch { try { } finally { throw; // CS0724 } } } static void Main() { } }  
```