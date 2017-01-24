---
title: "&#39;Loop&#39; 之前必須搭配相對應的 &#39;Do&#39; | Microsoft Docs"
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
  - "vbc30091"
  - "bc30091"
helpviewer_keywords: 
  - "BC30091"
ms.assetid: 05f47b2f-4eaa-4911-981e-3fce737d249f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Loop&#39; 之前必須搭配相對應的 &#39;Do&#39;
`Loop` 陳述式沒有相對應的 `Do` 陳述式。`Loop` 之前必須搭配相對應的 `Do` 陳述式。  
  
 **錯誤 ID︰**BC30091  
  
### 更正這個錯誤  
  
1.  如果這個 `Do` 迴圈是一組巢狀 `Do` 迴圈的一部分，請確定已正確地終止每個迴圈。  
  
2.  請確認已正確地終止 `Do` 迴圈內的其他控制結構。  
  
3.  請確定已正確地格式化這個 `Do` 迴圈。  
  
## 請參閱  
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)