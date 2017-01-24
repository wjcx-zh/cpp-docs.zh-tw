---
title: "可為 Null 的修飾詞不能配合隱含類型為 &#39;Object&#39; 的變數使用 | Microsoft Docs"
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
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 可為 Null 的修飾詞不能配合隱含類型為 &#39;Object&#39; 的變數使用
變數宣告中包含可為 Null 的類型修飾詞 \(?\)，但未指定類型或藉由指派值給宣告的變數來推斷類型。  
  
 **錯誤 ID︰**BC33112  
  
### 更正這個錯誤  
  
-   宣告可為 Null 的變數時，請指定類型。 類型不能為 <xref:System.Object>  
  
-   宣告可為 Null 的變數時，請指派值。 可為 Null 的變數的類型會從指派的值推斷。 值的類型不能是 <xref:System.Object>。  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)