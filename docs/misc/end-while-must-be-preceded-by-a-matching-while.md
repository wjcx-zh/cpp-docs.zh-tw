---
title: "&#39;End While&#39; 之前必須搭配相對應的 &#39;While&#39; | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End While&#39; 之前必須搭配相對應的 &#39;While&#39;
`End While` 陳述式沒有相對應的 `While` 陳述式。`End While` 之前必須搭配相對應的 `While` 陳述式。  
  
 **錯誤 ID：**BC30090  
  
### 更正這個錯誤  
  
1.  如果這個 `While` 區塊是一組巢狀 `While` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  請確認已正確地終止 `While` 區塊內的其他控制結構。  
  
3.  請確定已正確地格式化這個 `While` 區塊。  
  
## 請參閱  
 [While...End While Statement](../Topic/While...End%20While%20Statement%20\(Visual%20Basic\).md)