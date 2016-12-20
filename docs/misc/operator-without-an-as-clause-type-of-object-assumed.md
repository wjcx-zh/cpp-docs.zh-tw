---
title: "沒有 &#39;As&#39; 子句的運算子; 假設是 Object 的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有 &#39;As&#39; 子句的運算子; 假設是 Object 的類型
運算子程序未指定 `As` 子句。  
  
 `As` 子句會識別要與程式設計項目相關聯的資料類型。 在 [Operator Statement](../Topic/Operator%20Statement.md) 中，它會指定運算子程序傳回給呼叫端程式碼之值的資料類型。 如果您未在 `Operator` 陳述式中包含 `As` 子句，傳回資料類型會預設為 `Object`。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC41005  
  
### 更正這個錯誤  
  
-   請在 `Operator` 陳述式中包含 `As` 子句，以指定傳回資料類型。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)