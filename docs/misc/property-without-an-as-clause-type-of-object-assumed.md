---
title: "沒有 &#39;As&#39; 子句的屬性; 假設是 Object 的類型 | Microsoft Docs"
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
  - "BC42022"
  - "vbc42022"
helpviewer_keywords: 
  - "BC42022"
ms.assetid: 3379692b-8278-4488-878a-0afb76e554b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有 &#39;As&#39; 子句的屬性; 假設是 Object 的類型
屬性宣告未指定 `As` 子句。  
  
 `As` 子句會識別要與程式設計項目相關聯的資料類型。 在 [Property Statement](../Topic/Property%20Statement.md) 中，它會指定屬性 `Get` 程序傳回給呼叫端程式碼之值的資料類型。 如果您未在 `Property` 陳述式中包括 `As` 子句，屬性的資料類型會預設為 `Object`。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42022  
  
### 更正這個錯誤  
  
-   請在 `Property` 陳述式中包括 `As` 子句，以指定屬性的資料類型。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [Property Statement](../Topic/Property%20Statement.md)   
 [Get Statement](../Topic/Get%20Statement.md)