---
title: "&#39;&lt;邏輯運算子&gt;&#39; 的傳回類型與參數類型必須是 &#39;&lt;類型名稱&gt;&#39;，才可以用在 &#39;&lt;最少運算運算子&gt;&#39; 運算式中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33034"
  - "bc33034"
helpviewer_keywords: 
  - "BC33034"
ms.assetid: 94cd52dc-5d48-4673-b0b8-38a1954483c6
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;邏輯運算子&gt;&#39; 的傳回類型與參數類型必須是 &#39;&lt;類型名稱&gt;&#39;，才可以用在 &#39;&lt;最少運算運算子&gt;&#39; 運算式中
使用不適合的參數或傳回類別，宣告要在 [AndAlso Operator](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) 或 [OrElse Operator](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md) 中使用的 `And` 運算子或 `Or` 運算子。  
  
 因為您沒有直接定義最少運算運算子 \(`AndAlso` 或 `OrElse`\)，所以必須定義對應的邏輯和行列式運算子。 下表說明必要的運算子。  
  
|最少運算運算子|邏輯運算子|行列式運算子|  
|-------------|-----------|------------|  
|`AndAlso`|[And Operator](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse Operator](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or Operator](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue Operator](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 使用這些邏輯和行列式運算子來建構 `AndAlso` 或 `OrElse` 的最少運算邏輯。 若要讓此正常運作，您的 `And` 或 `Or` 定義的運算元和傳回值必須是包含的類型，也就是您正在定義 `And` 或 `Or` 的類別或結構的類型。  
  
 **錯誤 ID︰**BC33034  
  
### 更正這個錯誤  
  
-   請將兩個運算元和傳回值的類型變更為定義這個運算子之類別或結構的類型。  
  
     \-或\-  
  
-   請不要搭配使用對應的最少運算運算子 \(`AndAlso` 或 `OrElse`\) 與定義這個 `And` 或 `Or` 運算子之類別或結構的類型的運算元。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Logical and Bitwise Operators in Visual Basic](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)