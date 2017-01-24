---
title: "沒有 &#39;ReadOnly&#39; 或 &#39;WriteOnly&#39; 規範的 Property 必須提供 &#39;Get&#39; 和 &#39;Set&#39; | Microsoft Docs"
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
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 沒有 &#39;ReadOnly&#39; 或 &#39;WriteOnly&#39; 規範的 Property 必須提供 &#39;Get&#39; 和 &#39;Set&#39;
如果屬性未宣告為 `ReadOnly` 或 `WriteOnly`，則必須提供用於讀取及寫入其值的程序。  
  
 **錯誤 ID︰**BC30124  
  
### 更正這個錯誤  
  
1.  確定您在 `Property` 陳述式和 `End Property` 陳述式之間同時包含 `Get` 程序和 `Set` 程序。  
  
2.  請確認已正確地終止 `Property` 宣告內的其他程序。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Get Statement](../Topic/Get%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)