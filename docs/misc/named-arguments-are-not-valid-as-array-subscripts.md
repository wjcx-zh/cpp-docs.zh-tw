---
title: "具名引數不可以當做陣列註標 | Microsoft Docs"
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
  - "vbc30075"
  - "bc30075"
helpviewer_keywords: 
  - "BC30075"
ms.assetid: a25025c9-0763-4c19-9e9b-cffb9aacaa8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 具名引數不可以當做陣列註標
使用依名稱傳遞程序引數的語法，來指定陣列索引 \(例如 `Array(Index := 10)`\)。 這個語法不適用於陣列註標。  
  
 **錯誤 ID︰**BC30075  
  
### 更正這個錯誤  
  
-   使用一般變數或常數運算式作為陣列索引 \(例如 `Array(10)`\)。  
  
## 請參閱  
 [NOTINBUILD Visual Basic 中的陣列概觀](http://msdn.microsoft.com/zh-tw/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Passing Arguments by Position and by Name](../Topic/Passing%20Arguments%20by%20Position%20and%20by%20Name%20\(Visual%20Basic\).md)