---
title: "轉換運算子無法轉換為介面類型 | Microsoft Docs"
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
  - "vbc33025"
  - "bc33025"
helpviewer_keywords: 
  - "BC33025"
ms.assetid: 7e13dfa3-2b70-4ca6-a8ec-159131fd2c4c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉換運算子無法轉換為介面類型
轉換運算子宣告時，介面類型為傳回類型。  
  
 在編譯時期，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 會視為存在有從任何介面類型到任何介面的預先定義轉換。 這類轉換可能會在執行階段失敗，但編譯器無法預測執行階段結果，因此它可以編譯任何這類轉換。  
  
 因為編譯器認為已定義這項轉換，所以不允許您重新定義它。  
  
 **錯誤 ID︰**BC33025  
  
### 更正這個錯誤  
  
-   請完整移除這個運算子定義。 它已預先定義。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)