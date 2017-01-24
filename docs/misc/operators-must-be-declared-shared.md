---
title: "運算子必須宣告為 &#39;Shared&#39; | Microsoft Docs"
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
  - "vbc33012"
  - "bc33012"
helpviewer_keywords: 
  - "BC33012"
ms.assetid: 5ad97616-4032-46cd-aaf7-517db5d1195f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子必須宣告為 &#39;Shared&#39;
[Operator Statement](../Topic/Operator%20Statement.md) 不包含 [Shared](../Topic/Shared%20\(Visual%20Basic\).md) 關鍵字。  
  
 `Operator` 程序需要 [Public](../Topic/Public%20\(Visual%20Basic\).md) 和 `Shared` 兩個關鍵字，且轉換運算子也需要 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) 關鍵字。  
  
 **錯誤識別碼：**BC33012  
  
### 更正這個錯誤  
  
-   將 `Shared` 關鍵字加入 `Operator` 陳述式。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)