---
title: "&#39;Continue While&#39; 只可以在 &#39;While&#39; 陳述式中出現 | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue While&#39; 只可以在 &#39;While&#39; 陳述式中出現
`Continue While` 陳述式只可以在 `For...Next` 迴圈內出現。  
  
 **錯誤 ID︰**BC30784  
  
### 更正這個錯誤  
  
1.  如果 `Continue While` 陳述式是在 `Do...Loop` 迴圈內，請將陳述式變更為 `Continue Do`。  
  
2.  如果 `Continue While` 陳述式是在 `For...Next` 迴圈內，請將陳述式變更為 `Continue For`。  
  
3.  否則，請移除 `Continue While` 陳述式。  
  
## 請參閱  
 [Continue Statement](../Topic/Continue%20Statement%20\(Visual%20Basic\).md)   
 [While...End While Statement](../Topic/While...End%20While%20Statement%20\(Visual%20Basic\).md)