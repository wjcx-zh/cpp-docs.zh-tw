---
title: "此一元運算子的參數必須屬於包含類型 &#39;&lt;類型名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此一元運算子的參數必須屬於包含類型 &#39;&lt;類型名稱&gt;&#39;
一元運算子定義所指定參數的類型，不是定義運算子之類別或結構的類型。  
  
 當您在類別或結構中定義運算子時，至少有一個參數必須是該類別或結構的類型。 如果是一元運算子，則唯一的運算元必須是該類別或結構的類型。  
  
 **錯誤 ID︰**BC33020  
  
### 更正這個錯誤  
  
-   請將參數類型變更為定義運算子之類別或結構的類型。  
  
-   如果您想要採用一種資料類型作為參數，並傳回不同的資料類型作為作業結果，請改為定義轉換運算子。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)