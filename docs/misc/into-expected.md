---
title: "必須是 &#39;Into&#39; | Microsoft Docs"
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
  - "bc36615"
  - "vbc36615"
helpviewer_keywords: 
  - "BC36615"
ms.assetid: 24062dd9-a973-43b6-88d3-c11adc5a3736
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;Into&#39;
指定的 `Aggregate`、`Group By` 或 `Group Join` 子句未使用 `Into` 運算子。 您可以使用 `Into` 運算子來識別要套用至查詢結果的彙總函式，以及識別要包含分組結果的查詢結果類型成員 \(透過使用 `Group` 彙總函式\)。  
  
 **錯誤 ID︰**BC36615  
  
### 更正這個錯誤  
  
1.  將 `Into` 運算子加入 `Aggregate`、`Group By` 或 `Group Join` 子句。 以下是一個範例：  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## 請參閱  
 [Aggregate Clause](../Topic/Aggregate%20Clause%20\(Visual%20Basic\).md)   
 [Group By 子句](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)