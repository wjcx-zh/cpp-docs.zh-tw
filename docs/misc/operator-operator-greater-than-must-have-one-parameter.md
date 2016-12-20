---
title: "運算子 &#39;&lt;運算子&gt;&#39; 必須有一個參數 | Microsoft Docs"
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
  - "bc33014"
  - "vbc33014"
helpviewer_keywords: 
  - "BC33014"
ms.assetid: 512a5724-a6c5-4437-a608-7d6b10e68d49
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子 &#39;&lt;運算子&gt;&#39; 必須有一個參數
一元運算子的定義不含任何參數，或是具有多個參數。  
  
 一元運算子必須剛好只有一個參數。  
  
 **錯誤 ID︰**BC33014  
  
### 更正這個錯誤  
  
-   請調整定義，以指定剛好一個參數。  
  
-   如果您需要兩個參數，必須定義二元運算子。  
  
-   如果您不需要任何參數，或需要兩個以上的參數，則必須使用 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 來定義 `Function` 程序，而不是運算子。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)