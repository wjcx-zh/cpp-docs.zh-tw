---
title: "&#39;While&#39; 之後必須搭配相對應的 &#39;End While&#39; | Microsoft Docs"
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
  - "bc30082"
  - "vbc30082"
helpviewer_keywords: 
  - "BC30082"
ms.assetid: 50b722b1-906f-4cb1-b5d4-fefab2ba3907
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;While&#39; 之後必須搭配相對應的 &#39;End While&#39;
`While` 陳述式沒有相對應的 `End While` 陳述式。 必須使用 `End While` 陳述式來結束 `While` 區塊。  
  
 **錯誤 ID︰**BC30082  
  
### 更正這個錯誤  
  
1.  如果這個 `While` 區塊是一組巢狀 `While` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  將 `End While` 陳述式加入 `While` 區塊的結尾。  
  
## 請參閱  
 [While...End While Statement](../Topic/While...End%20While%20Statement%20\(Visual%20Basic\).md)