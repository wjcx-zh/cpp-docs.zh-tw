---
title: "必須有關係運算子 | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須有關係運算子
`Case` 陳述式包含 `Is` 子句，但沒有比較運算子 \(如 `=` 或 `>`\)。 如果 `Case` 陳述式不包括運算子，則會採用 `=`，而且不會使用 `Is`。  
  
 **錯誤 ID︰**BC30239  
  
### 更正這個錯誤  
  
-   請移除 `Is` 關鍵字，或在它的後面加上比較運算子。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)   
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [Comparison Operators](../Topic/Comparison%20Operators%20\(Visual%20Basic\).md)