---
title: "方法主體的第一個陳述式不可以和方法宣告在同一行上 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30040"
  - "bc30040"
helpviewer_keywords: 
  - "BC30040"
ms.assetid: 27df3488-de77-499d-b9a6-08037d540cb0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法主體的第一個陳述式不可以和方法宣告在同一行上
`Function`、`Sub`、`Get`、`Set` 或 `Property` 陳述式必須單獨在原始程式碼行上。  
  
 **錯誤 ID︰**BC30040  
  
### 更正這個錯誤  
  
1.  移除程序宣告之前的任何行標籤。  
  
2.  將程序宣告之前的任何陳述式都移至前一個原始程式碼行。  
  
3.  將程序宣告之後的任何陳述式都移至後一個原始程式碼行。  
  
## 請參閱  
 [Procedures](../Topic/Procedures%20in%20Visual%20Basic.md)   
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)