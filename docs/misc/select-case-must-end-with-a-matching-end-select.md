---
title: "&#39;Select Case&#39; 的結尾必須是相對應的 &#39;End Select&#39; | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select Case&#39; 的結尾必須是相對應的 &#39;End Select&#39;
`Select` 或 `Select Case` 陳述式沒有相對應的 `End Select` 陳述式。 必須使用 `End Select` 陳述式來結束 `Select` 區塊。  
  
 **錯誤 ID︰**BC30095  
  
### 更正這個錯誤  
  
1.  如果這個 `Select` 區塊是一組巢狀 `Select` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  將 `End Select` 陳述式加入 `Select` 區塊的結尾。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)