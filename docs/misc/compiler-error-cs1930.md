---
title: "編譯器錯誤 CS1930 | Microsoft Docs"
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
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1930
已經宣告範圍變數 'name'  
  
 除非查詢運算式終止，否則查詢運算式中的範圍變數位於範圍中。 因此，它必須有唯一的識別項。  
  
### 更正這個錯誤  
  
1.  請為查詢運算式中引進的每個範圍變數提供唯一名稱。  
  
## 範例  
 下列範例會產生 CS1930，因為識別項 `num` 是用於 `from` 子句中的範圍變數，以及是用於 `let` 子句引進的範圍變數。  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)