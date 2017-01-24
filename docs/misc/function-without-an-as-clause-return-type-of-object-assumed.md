---
title: "沒有 &#39;As&#39; 子句的函式; 假設是 Object 的傳回類型 | Microsoft Docs"
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
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有 &#39;As&#39; 子句的函式; 假設是 Object 的傳回類型
`Function` 程序未指定 `As` 子句。  
  
 `As` 子句會識別要與程式設計項目相關聯的資料類型。 在 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 中，它會指定 `Function` 程序傳回給呼叫端程式碼之值的資料類型。 如果您未在 `Function` 陳述式中包含 `As` 子句，傳回資料類型會預設為 `Object`。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42021  
  
### 更正這個錯誤  
  
-   請在 `Function` 陳述式中包含 `As` 子句，以指定傳回資料類型。  
  
## 請參閱  
 [函式程序](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)