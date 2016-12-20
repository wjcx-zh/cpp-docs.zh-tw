---
title: "&#39;Continue Do&#39; 只可以在 &#39;Do&#39; 陳述式中出現 | Microsoft Docs"
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
  - "vbc30782"
  - "bc30782"
helpviewer_keywords: 
  - "BC30782"
ms.assetid: c6b35e63-4d84-449d-9685-41a1bc0a7f35
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue Do&#39; 只可以在 &#39;Do&#39; 陳述式中出現
`Continue Do` 陳述式只可以在 `Do...Loop` 迴圈內出現。  
  
 **錯誤 ID︰**BC30782  
  
### 更正這個錯誤  
  
1.  如果 `Continue Do` 陳述式是在 `For...Next` 迴圈內，請將陳述式變更為 `Continue For`。  
  
2.  如果 `Continue Do` 陳述式是在 `While...End While` 迴圈內，請將陳述式變更為 `Continue While`。  
  
3.  否則，請移除 `Continue Do` 陳述式。  
  
## 請參閱  
 [Continue Statement](../Topic/Continue%20Statement%20\(Visual%20Basic\).md)   
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)