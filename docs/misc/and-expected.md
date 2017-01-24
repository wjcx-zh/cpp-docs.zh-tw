---
title: "必須是 &#39;And&#39; | Microsoft Docs"
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
  - "vbc36620"
  - "bc36620"
helpviewer_keywords: 
  - "BC36620"
ms.assetid: b3d21d4d-86c0-44d2-8afc-c19d375e9ddd
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;And&#39;
使用了 `And` 以外的比較運算子來結合 `Join` 或 `Group Join` 子句中的兩個或多個 `Equals` 運算子。 只有 `And` 運算子可以與 `Join` 或 `Group Join` 子句中的多個 `Equals` 運算子結合。  
  
 **錯誤 ID︰**BC36620  
  
### 更正這個錯誤  
  
1.  只使用 `And` 運算子來重建 `Equals` 子句進行比較。 以下是一個範例：  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _  
                        Join pet In pets _  
                        On pet.Owner Equals pers And _  
                           pet.Name = pers.PetName_  
                        Select pers, pet  
    ```  
  
## 請參閱  
 [How to: Combine Data with Joins](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join Clause](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)