---
title: "Structure 中的非共用成員不可以宣告為 &#39;New&#39; | Microsoft Docs"
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
  - "vbc30795"
  - "BC30795"
helpviewer_keywords: 
  - "BC30795"
ms.assetid: 8e4e1ad8-3bac-475f-82e8-e4f134692204
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure 中的非共用成員不可以宣告為 &#39;New&#39;
在結構中使用 `New` 子句宣告非共用變數。  
  
 您可以初始化結構中的共用參考變數，也可以擁有非共用參考變數而不進行初始化，如下列程式碼行所示。  
  
 `Shared structVar1 As New System.ApplicationException`  
  
 `Dim structVar2 As System.ApplicationException`  
  
 不過，您無法初始化結構中的非共用參考變數。 下列程式碼行無效。  
  
 `Dim structVar3 As New System.ApplicationException ' INVALID IN A STRUCTURE`  
  
 **錯誤 ID︰**BC30795  
  
### 更正這個錯誤  
  
-   從參考變數宣告中移除 `Shared` 修飾詞或 `New` 關鍵字。  
  
## 請參閱  
 [Structure Statement](../Topic/Structure%20Statement.md)   
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)