---
title: "編譯器錯誤 CS1947 | Microsoft Docs"
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
  - "CS1947"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1947"
ms.assetid: e2822fba-a176-4466-9cdc-63c44e22ebcb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1947
無法指派範圍變數 'variable name' \-\- 其為唯讀。  
  
 範圍變數就像 `foreach` 陳述式中的反覆項目變數。 它不能在查詢運算式中指派。  
  
### 更正這個錯誤  
  
1.  請移除範圍變數的指派。  
  
2.  必要時，請使用 `let` 子句來引進新的範圍變數，並使用它來儲存值。  
  
## 範例  
 下列程式碼會產生 CS1947：  
  
```  
// cs1947.cs using System.Linq; class Test { static void Main() { int[] array = new int[] { 1, 2, 3, 4, 5 }; var x = from i in array let k = i select i = 5; // CS1947 x.ToList(); } }  
```  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)