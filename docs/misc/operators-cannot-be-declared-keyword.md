---
title: "運算子不可宣告為 &#39;&lt;關鍵字&gt;&#39; | Microsoft Docs"
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
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子不可宣告為 &#39;&lt;關鍵字&gt;&#39;
使用對運算子定義無效的關鍵字來宣告運算子。  
  
 每個運算子都必須宣告為 [Public](../Topic/Public%20\(Visual%20Basic\).md) 和 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)。 此外，必須使用 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) 來宣告轉換運算子，但不可同時使用兩者。 運算子定義可以選擇性地包含 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 或 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 關鍵字。[Operator Statement](../Topic/Operator%20Statement.md) 中不允許其他關鍵字。  
  
 **錯誤 ID︰**BC33013  
  
### 更正這個錯誤  
  
-   請從運算子定義中移除無效的關鍵字。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)