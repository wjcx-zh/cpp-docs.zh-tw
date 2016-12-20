---
title: "運算子 &#39;&lt;運算子&gt;&#39; 必須擁有布林傳回類型 | Microsoft Docs"
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
  - "vbc33023"
  - "bc33023"
helpviewer_keywords: 
  - "BC33023"
ms.assetid: 18e066f4-d71e-4e38-b0bc-8af9145f6015
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子 &#39;&lt;運算子&gt;&#39; 必須擁有布林傳回類型
比較或邏輯運算子宣告時的傳回類型不是[Boolean Data Type](../Topic/Boolean%20Data%20Type%20\(Visual%20Basic\).md)。  
  
 比較運算子 \(`=`、`<>`、`<`、`<=`、`>`、`>=`、`Is`、`IsNot`、`IsFalse`、`IsTrue`、`Like`、`TypeOf`\) 的結果只能是 `True` 或 `False`。 如需詳細資訊，請參閱[Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)。  
  
 邏輯運算子 \(`And`、`AndAlso`、`Not`、`Or`、`OrElse`、`Xor`\) 完全在布林值的定義域內運作。 如需詳細資訊，請參閱[Logical and Bitwise Operators in Visual Basic](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC33023  
  
### 更正這個錯誤  
  
-   請將此比較或邏輯運算子的傳回類型取代為 `Boolean`。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)