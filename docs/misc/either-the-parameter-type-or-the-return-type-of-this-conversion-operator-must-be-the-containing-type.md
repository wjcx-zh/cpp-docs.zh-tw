---
title: "此轉換運算子的參數類型或傳回類型必須是包含類型 | Microsoft Docs"
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
  - "vbc33022"
  - "bc33022"
helpviewer_keywords: 
  - "BC33022"
ms.assetid: 55baff11-eb35-4c81-bc04-5006524ab450
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此轉換運算子的參數類型或傳回類型必須是包含類型
轉換運算子定義所指定參數和傳回類型的類型，不是定義運算子之類別或結構的類型。  
  
 當您在類別或結構中定義轉換運算子時，它必須轉換成該類別或結構的類型，或從該類別或結構的類型進行轉換。  
  
 **錯誤 ID︰**BC33022  
  
### 更正這個錯誤  
  
-   請將參數類型或傳回類型變更為定義運算子之類別或結構的類型。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)