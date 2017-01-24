---
title: "編譯器錯誤 CS1017 | Microsoft Docs"
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
  - "CS1017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1017"
ms.assetid: e0902e8a-b042-4711-a8a6-83456a3f88cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1017
Catch 子句無法接在 try 陳述式的一般 catch 字句之後  
  
 未採用任何參數的 `catch` 區塊必須是一系列 `catch` 區塊的最後一個區塊。 如需例外狀況的詳細資訊，請參閱 [例外狀況處理陳述式](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)。  
  
## 範例  
 下列範例會產生 CS1017：  
  
```  
// CS1017.cs using System; namespace x { public class b : Exception { } public class a { public static void Main() { try { } catch   // CS1017, must be last catch { } catch(b) { throw; } } } }  
```