---
title: "&#39;ReadOnly&#39; 變數不可以是指派的目標 | Microsoft Docs"
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
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; 變數不可以是指派的目標
`ReadOnly` 屬性出現在指派其值的內容中。 在執行期間，只會指派可寫入變數、屬性和陣列項目的值。  
  
 **錯誤 ID︰**BC30064  
  
### 更正這個錯誤  
  
-   從宣告變數的 `Dim` 陳述式中移除 `ReadOnly` 關鍵字，或移除指派給它值的陳述式。  
  
## 請參閱  
 [ReadOnly](../Topic/ReadOnly%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)