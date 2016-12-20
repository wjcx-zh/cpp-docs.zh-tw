---
title: "轉型運算子中的語法錯誤; 兩個引數之間必須以逗號分隔 | Microsoft Docs"
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
  - "vbc30944"
  - "bc30944"
helpviewer_keywords: 
  - "BC30944"
ms.assetid: 1f7ed4a1-6ff5-4836-8424-21618c68ff45
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 轉型運算子中的語法錯誤; 兩個引數之間必須以逗號分隔
運算式使用 `CType` 轉換函式，或是使用 `DirectCast` 或 `TryCast` 轉換關鍵字，但只提供一個引數。  
  
 `CType`、`DirectCast` 和 `TryCast` 都需要兩個引數。 第一個引數是要轉換的運算式，而第二個引數是轉換的目標資料類型或類別類型。  
  
 **錯誤 ID︰**BC30944  
  
### 更正這個錯誤  
  
-   視需要提供兩個引數以進行轉換。  
  
-   如果您想要使用其中一個特定 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md) \(例如 `CString`\)，則必須使用該函式名稱，而不是 `CType`。 然後只需要一個引數。  
  
## 請參閱  
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)