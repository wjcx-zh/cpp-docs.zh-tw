---
title: "&#39;If&#39; 之後必須搭配相對應的 &#39;End If&#39; | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; 之後必須搭配相對應的 &#39;End If&#39;
`If` 陳述式沒有相對應的 `End If` 陳述式。 必須使用 `End If` 陳述式來結束 `If` 區塊。  
  
 **錯誤 ID︰**BC30081  
  
### 更正這個錯誤  
  
1.  如果這個 `If` 區塊是一組巢狀 `If` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  將 `End If` 陳述式加入 `If` 區塊的結尾。  
  
## 請參閱  
 [If...Then...Else Statement](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)