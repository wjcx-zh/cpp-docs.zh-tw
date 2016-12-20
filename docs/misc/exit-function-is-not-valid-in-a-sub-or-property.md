---
title: "Sub 或 Property 中的 &#39;Exit Function&#39; 無效 | Microsoft Docs"
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
  - "vbc30067"
  - "bc30067"
helpviewer_keywords: 
  - "BC30067"
ms.assetid: 207fef65-4383-4120-9e5a-e0e14d168a72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub 或 Property 中的 &#39;Exit Function&#39; 無效
`Exit Function` 出現在 `Sub` 程序或 `Property` 程序。`Exit` 陳述式必須符合它發生所在的區塊。  
  
 **錯誤 ID︰**BC30067  
  
### 更正這個錯誤  
  
-   請視需要將 `Exit Function` 取代為 `Exit Sub` 或 `Exit Property` 陳述式。  
  
## 請參閱  
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [函式程序](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)