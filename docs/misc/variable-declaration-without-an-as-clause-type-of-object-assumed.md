---
title: "沒有 &#39;As&#39; 子句的變數宣告; 假設是 Object 的類型 | Microsoft Docs"
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
  - "BC42020"
  - "vbc42020"
helpviewer_keywords: 
  - "BC42020"
ms.assetid: 9422b16d-39b5-4d49-b697-608226ccafea
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有 &#39;As&#39; 子句的變數宣告; 假設是 Object 的類型
變數宣告未指定 `As` 子句。  
  
 `As` 子句會識別要與程式設計項目相關聯的資料類型。 在 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md) 中，它會指定一個或多個變數的資料類型。 如果您未在 `Dim` 陳述式中包含 `As` 子句，變數的資料類型會預設為 `Object`。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC42020  
  
### 更正這個錯誤  
  
-   請在 `Dim` 陳述式中包含 `As` 子句，以指定變數的資料類型。  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [變數宣告](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)