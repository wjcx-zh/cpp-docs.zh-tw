---
title: "編譯器錯誤 CS1949 | Microsoft Docs"
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
  - "CS1949"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1949"
ms.assetid: 959f553e-ac3d-43a1-b0a0-11e270f2ad64
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1949
無法在範圍變數宣告中使用內容關鍵字 'var'。  
  
 範圍變數是由編譯器所隱含輸入。 不需要搭配使用 [var](../Topic/var%20\(C%23%20Reference\).md) 與範圍變數。  
  
### 更正這個錯誤  
  
1.  請移除範圍變數前面的 `var`  關鍵字。  
  
## 範例  
 下列範例會產生 CS1949：  
  
```  
// cs1949.cs using System; using System.Linq; class Test { static void Main() { var x = from var i in Enumerable.Range(1, 100) // CS1949 select i; } }  
```  
  
## 請參閱  
 [LINQ 查詢運算式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)   
 [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)