---
title: "&#39;End If&#39; 之前必須搭配相對應的 &#39;If&#39; | Microsoft Docs"
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
  - "bc30087"
  - "vbc30087"
helpviewer_keywords: 
  - "BC30087"
ms.assetid: 81c056bb-267e-44ef-9a44-3a41273090ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End If&#39; 之前必須搭配相對應的 &#39;If&#39;
`End If` 陳述式沒有相對應的 `If` 陳述式。`End If` 之前必須搭配 `If` 陳述式。  
  
 **錯誤識別碼：**BC30087  
  
### 更正這個錯誤  
  
1.  如果這個 `If` 區塊是一組巢狀 `If` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  請確認已正確地終止 `If` 區塊內的其他控制結構。  
  
3.  請確定已正確地格式化這個 `If` 區塊。  
  
## 請參閱  
 [If...Then...Else Statement](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)