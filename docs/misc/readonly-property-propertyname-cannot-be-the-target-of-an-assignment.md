---
title: "&#39;ReadOnly&#39; 屬性 &#39;&lt;屬性名稱&gt;&#39; 不可以是指派的目標 | Microsoft Docs"
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
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; 屬性 &#39;&lt;屬性名稱&gt;&#39; 不可以是指派的目標
`ReadOnly` 屬性會發生在指派其值的內容中。 在執行期間，只會指派可寫入變數、屬性和陣列項目的值。  
  
 **錯誤 ID︰**BC30098  
  
### 更正這個錯誤  
  
-   從宣告變數的 `Property` 陳述式中移除 `ReadOnly` 關鍵字，或移除將值指派給它的陳述式。  
  
## 請參閱  
 [ReadOnly](../Topic/ReadOnly%20\(Visual%20Basic\).md)   
 [Property Statement](../Topic/Property%20Statement.md)