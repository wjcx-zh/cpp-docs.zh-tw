---
title: "必須是常數運算式 | Microsoft Docs"
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
  - "bc30059"
  - "vbc30059"
helpviewer_keywords: 
  - "BC30059"
ms.assetid: fdd5e7bb-6370-4a63-bbb6-23b15badb4c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是常數運算式
`Const` 陳述式未正確初始化常數，或陣列宣告使用變數來指定項目數。  
  
 **錯誤 ID︰**BC30059  
  
### 更正這個錯誤  
  
1.  如果宣告是 `Const` 陳述式，請確定此常數是以常值、先前宣告的常數、列舉成員，或常值、常數和列舉成員的組合結合運算子來進行初始化。  
  
2.  如果宣告指定陣列，請檢查是否使用了變數來指定項目數。 如果是，請以常數運算式取代變數。  
  
## 請參閱  
 [Const Statement](../Topic/Const%20Statement%20\(Visual%20Basic\).md)   
 [NOTINBUILD 陣列變數](http://msdn.microsoft.com/zh-tw/c2da78bd-6928-46ba-805f-44f819dfaf93)