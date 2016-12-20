---
title: "運算子 &#39;&lt;運算子&gt;&#39; 必須有一個或兩個參數 | Microsoft Docs"
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
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 運算子 &#39;&lt;運算子&gt;&#39; 必須有一個或兩個參數
可以是一元或二元的運算子在定義時不含任何參數，或具有兩個以上的參數。  
  
 一元\/二元運算子必須有一個或兩個參數。  
  
 **錯誤 ID︰**BC33016  
  
### 更正這個錯誤  
  
-   請調整定義，以指定一個或兩個參數。  
  
-   如果您不需要任何參數，或需要兩個以上的參數，則必須使用 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 來定義 `Function` 程序，而不是運算子。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)