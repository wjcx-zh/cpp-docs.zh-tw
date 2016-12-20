---
title: "運算子必須宣告為 &#39;Public&#39; | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子必須宣告為 &#39;Public&#39;
[Operator Statement](../Topic/Operator%20Statement.md) 不包含 [Public](../Topic/Public%20\(Visual%20Basic\).md) 關鍵字。  
  
 `Operator` 程序需要 `Public` 和 [Shared](../Topic/Shared%20\(Visual%20Basic\).md) 兩個關鍵字，且轉換運算子也需要 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) 關鍵字。  
  
 **錯誤 ID：**BC33011  
  
### 更正這個錯誤  
  
-   將 `Public` 關鍵字加入 `Operator` 陳述式。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)