---
title: "&#39;Handles&#39; 在運算子宣告中無效 | Microsoft Docs"
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
  - "bc33003"
  - "vbc33003"
helpviewer_keywords: 
  - "BC33003"
ms.assetid: 8336402c-9393-4e8e-834d-55c2268f24f6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; 在運算子宣告中無效
[Operator Statement](../Topic/Operator%20Statement.md) 指定 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md) 關鍵字。  
  
 只有 `Sub` 程序可以處理事件，`Operator` 程序則無法。 如需事件處理常式的詳細資訊，請參閱[How to: Call an Event Handler in Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md)。  
  
 `Operator` 程序需要 `Public` 和 `Shared` 關鍵字，而轉換運算子需要 `Widening` 或 `Narrowing` 關鍵字。 如需詳細資訊，請參閱[Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC33003  
  
### 更正這個錯誤  
  
-   如果您想要讓這個程序處理事件，請將其重寫為 `Sub` 程序。  
  
-   如果您想要讓這個程序定義運算子，請從其宣告移除 `Handles` 關鍵字。  
  
## 請參閱  
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)