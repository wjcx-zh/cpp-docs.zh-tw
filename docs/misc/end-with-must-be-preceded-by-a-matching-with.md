---
title: "&#39;End With&#39; 之前必須搭配相對應的 &#39;With&#39; | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End With&#39; 之前必須搭配相對應的 &#39;With&#39;
`End With` 陳述式沒有相對應的 `With` 陳述式。`End With` 之前必須搭配相對應的 `With` 陳述式。  
  
 **錯誤 ID︰**BC30093  
  
### 更正這個錯誤  
  
1.  如果這個 `With` 區塊是一組巢狀 `With` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  請確認已正確地終止 `With` 區塊內的其他控制結構。  
  
3.  請確定已正確地格式化這個 `With` 區塊。  
  
## 請參閱  
 [With...End With Statement](../Topic/With...End%20With%20Statement%20\(Visual%20Basic\).md)