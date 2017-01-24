---
title: "編譯器錯誤 CS1524 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1524"
ms.assetid: a7b80bbc-a2de-4718-b0f0-4c9526726525
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1524
必須是 catch 或 finally  
  
 `try` 區塊後面必須有 `catch` 或 `finally` 區塊。  
  
 如需例外狀況的詳細資訊，請參閱 [例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)。  
  
## 範例  
 下列範例會產生 CS1524：  
  
```  
// CS1524.cs class x { public static void Main() { try { // Code here } catch { } try { // Code here } finally { } try { // Code here } }     // CS1524, missing catch or finally }  
```