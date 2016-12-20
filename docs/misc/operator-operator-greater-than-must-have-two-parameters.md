---
title: "運算子 &#39;運算子&gt;&#39; 必須有兩個參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子 &#39;運算子&gt;&#39; 必須有兩個參數
已定義少於兩個或多於兩個參數的二元運算子。  
  
 二元運算子必須剛好有兩個參數。  
  
 **錯誤 ID︰**BC33015  
  
### 更正這個錯誤  
  
-   請調整定義，以指定剛好兩個參數。  
  
-   如果您只需要一個參數，您必須定義一元運算子。  
  
-   如果您不需要任何參數，或需要兩個以上的參數，則必須使用 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 來定義 `Function` 程序，而不是運算子。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)