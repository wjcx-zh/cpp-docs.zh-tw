---
title: "必須是 &#39;On&#39; | Microsoft Docs"
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
  - "bc36618"
  - "vbc36618"
helpviewer_keywords: 
  - "BC36618"
ms.assetid: 7cb1b205-c4c3-4485-ae3f-8942425692ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;On&#39;
指定的 `Join` 或 `Group Join` 子句未使用 `On` 運算子。 您使用 `On` 運算子來識別每個集合的範圍變數的索引鍵欄位。 索引鍵欄位用來比對每個集合的項目。  
  
 **錯誤 ID︰**BC36618  
  
### 更正這個錯誤  
  
1.  請將 `On` 運算子和索引鍵欄位加入 `Join` 或 `Group Join` 子句中。 以下是一個範例：  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _ Join pet In pets _ On pet.Owner Equals pers _ Select pers.FirstName, PetName = pet.Name  
    ```  
  
## 請參閱  
 [How to: Combine Data with Joins](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join Clause](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)