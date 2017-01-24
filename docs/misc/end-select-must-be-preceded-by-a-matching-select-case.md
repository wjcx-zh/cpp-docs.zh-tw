---
title: "&#39;End Select&#39; 之前必須搭配相對應的 &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Select&#39; 之前必須搭配相對應的 &#39;Select Case&#39;
`End Select` 陳述式沒有相對應的 `Select` 或 `Select Case` 陳述式。`End Select` 之前必須搭配 `Select` 或 `Select Case` 陳述式。  
  
 **錯誤 ID︰**BC30088  
  
### 更正這個錯誤  
  
1.  如果這個 `Select` 區塊是一組巢狀 `Select` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  請確認已正確地終止 `Select` 區塊內的其他控制結構。  
  
3.  請確認已正確地格式化這個 `Select` 區塊。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)