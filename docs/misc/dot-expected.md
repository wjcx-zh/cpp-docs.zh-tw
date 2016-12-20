---
title: "必須是 &#39;.&#39; | Microsoft Docs"
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
  - "bc30287"
  - "vbc30287"
helpviewer_keywords: 
  - "BC30287"
ms.assetid: 7d7b4934-b521-4ed3-b054-aeb71f8daacf
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;.&#39;
程式碼有 `Handles` 子句，其中包含一個驚嘆號 \(`!`\)。  
  
 **錯誤 ID︰**BC30287  
  
### 更正這個錯誤  
  
1.  如果 `Handles` 子句參考物件內的事件，請使用句號 \(`.`\) 來分隔物件與事件。  
  
     這個範例會處理來自 `Button1` 物件的 `Click` 事件。  
  
     [!code-vb[VbVbalrEventError#21](../misc/codesnippet/VisualBasic/dot-expected_1.vb)]  
  
## 請參閱  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)