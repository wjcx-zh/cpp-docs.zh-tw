---
title: "必須是 &#39;Group&#39; 或識別項 | Microsoft Docs"
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
  - "vbc36707"
  - "bc36707"
helpviewer_keywords: 
  - "BC36707"
ms.assetid: 214e4aa3-d20f-41b3-902c-f1076d31b832
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;Group&#39; 或識別項
`Group By` 或 `Group Join` 子句的 `Into` 部分不包含 `Group` 關鍵字。 您必須在 `Group By` 或 `Group Join` 子句的 `Into` 子句中包含 `Group` 關鍵字，以識別用於群組結果的變數名稱。 這可以是您指定的名稱或關鍵字 `Group`。  
  
 **錯誤 ID︰**BC36707  
  
### 更正這個錯誤  
  
1.  確定 `Group By` 或 `Group Join` 子句的 `Into` 部分包含 `Group` 關鍵字，如下列範例所示。  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [Group By 子句](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)