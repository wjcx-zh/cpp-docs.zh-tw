---
title: "轉換運算子必須宣告為 &#39;Widening&#39; 或 &#39;Narrowing&#39;。 | Microsoft Docs"
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
  - "vbc33017"
  - "bc33017"
helpviewer_keywords: 
  - "BC33017"
ms.assetid: 5972d955-ce1d-4348-a021-167eecb3a507
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉換運算子必須宣告為 &#39;Widening&#39; 或 &#39;Narrowing&#39;。
[Operator Statement](../Topic/Operator%20Statement.md) 未指定 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md)。  
  
 當您定義轉換運算子時，必須將它宣告為 `Widening` 或 `Narrowing`。 這些特性是互斥的，因此您無法同時指定兩者。  
  
 **錯誤識別碼：**BC33017  
  
### 更正這個錯誤  
  
-   決定轉換運算子是 `Widening` 或 `Narrowing`，並在 `Operator` 陳述式中包含適當的關鍵字。 您必須指定其中一個。  
  
## 請參閱  
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)