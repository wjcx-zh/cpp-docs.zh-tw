---
title: "Function 或 Property 中的 &#39;Exit Sub&#39; 無效 | Microsoft Docs"
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
  - "bc30065"
  - "vbc30065"
helpviewer_keywords: 
  - "BC30065"
ms.assetid: d6426861-ba64-4dca-9100-262c6c058bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function 或 Property 中的 &#39;Exit Sub&#39; 無效
`Exit Sub` 出現在 `Function` 程序或 `Property` 程序。`Exit` 陳述式必須符合它發生所在的區塊。  
  
 **錯誤 ID︰**BC30065  
  
### 更正這個錯誤  
  
-   請視需要將 `Exit Sub` 取代為 `Exit Function` 或 `Exit Property` 陳述式。  
  
## 請參閱  
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [函式程序](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)