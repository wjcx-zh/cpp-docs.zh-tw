---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 必須定義要在 &#39;&lt;最少運算運算子&gt;&#39; 運算式中使用的運算子 &#39;&lt;行列式運算子&gt;&#39; | Microsoft Docs"
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
  - "bc33035"
  - "vbc33035"
helpviewer_keywords: 
  - "BC33035"
ms.assetid: 50a0a39f-63cd-4100-aea9-91b5b6ab5bbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 必須定義要在 &#39;&lt;最少運算運算子&gt;&#39; 運算式中使用的運算子 &#39;&lt;行列式運算子&gt;&#39;
[AndAlso Operator](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) 或 [OrElse Operator](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md) 使用類別或結構類型的運算元，但類別或結構並未定義所需的運算子。  
  
 因為您沒有直接定義最少運算運算子 \(`AndAlso` 或 `OrElse`\)，所以必須定義對應的邏輯和行列式運算子。 下表說明必要的運算子。  
  
|最少運算運算子|邏輯運算子|行列式運算子|  
|-------------|-----------|------------|  
|`AndAlso`|[And Operator](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse Operator](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or Operator](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue Operator](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 使用這些邏輯和行列式運算子來建構 `AndAlso` 或 `OrElse` 的最少運算邏輯。 若要讓此正常運作，您的 `And` 或 `Or` 定義的運算元和傳回值必須是包含的類型，也就是您正在定義 `And` 或 `Or` 的類別或結構的類型。  
  
 **錯誤 ID︰**BC33035  
  
### 更正這個錯誤  
  
-   請在 `AndAlso` 或 `OrElse` 運算子運算元類型所使用的類別或結構中，定義 `And` 和 `IsFalse` 運算子，或 `Or` 和 `IsTrue` 運算子。`And` 或 `Or` 的運算元務必要是屬於您定義它的類別或結構的類型。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Logical and Bitwise Operators in Visual Basic](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)