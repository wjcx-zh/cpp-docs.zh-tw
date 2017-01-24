---
title: "&#39;Do&#39; 之後必須搭配相對應的 &#39;Loop&#39; | Microsoft Docs"
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
  - "vbc30083"
  - "bc30083"
helpviewer_keywords: 
  - "BC30083"
ms.assetid: b157b9e3-57fa-4324-a13d-b37bcf0861e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Do&#39; 之後必須搭配相對應的 &#39;Loop&#39;
`Do` 陳述式沒有相對應的 `Loop` 陳述式。 必須使用 `Loop` 陳述式來結束 `Do` 迴圈。  
  
 **錯誤 ID︰**BC30083  
  
### 更正這個錯誤  
  
-   如果這個 `Do` 迴圈是一組巢狀迴圈的一部分，請確定已正確地終止每個迴圈。  
  
-   將 `Loop` 陳述式加入 `Do` 迴圈的結尾。  
  
## 請參閱  
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)