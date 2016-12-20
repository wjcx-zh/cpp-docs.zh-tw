---
title: "必須是 &#39;In&#39; | Microsoft Docs"
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
  - "bc36607"
  - "vbc36607"
helpviewer_keywords: 
  - "BC36607"
ms.assetid: f390bca5-12fe-4fe1-bd86-7f8ab66dfbd8
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;In&#39;
指定的 `From` 或 `Aggregate` 子句未使用 `In` 運算子。 您會使用 `In` 運算子來識別要查詢的集合。  
  
 **錯誤 ID︰**BC36607  
  
### 更正這個錯誤  
  
1.  請將 `In` 運算子和索引鍵欄位加入 `From` 或 `Aggregate` 子句中。 以下是一個範例：  
  
    ```vb#  
    Dim names = From pers In people Select pers.FirstName, pers.LastName  
    ```  
  
## 請參閱  
 [From Clause](../Topic/From%20Clause%20\(Visual%20Basic\).md)   
 [Aggregate Clause](../Topic/Aggregate%20Clause%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)