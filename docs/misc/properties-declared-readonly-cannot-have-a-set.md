---
title: "宣告為 &#39;ReadOnly&#39; 的屬性不能有 &#39;Set&#39; | Microsoft Docs"
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
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 宣告為 &#39;ReadOnly&#39; 的屬性不能有 &#39;Set&#39;
`Set` 程序會寫入屬性的值。 無法寫入 `ReadOnly` 屬性。  
  
 **錯誤 ID︰**BC30022  
  
### 更正這個錯誤  
  
-   請從 `Property` 陳述式中移除 `ReadOnly` 關鍵字，或從屬性主體中移除 `Set` 程序。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)   
 [ReadOnly](../Topic/ReadOnly%20\(Visual%20Basic\).md)