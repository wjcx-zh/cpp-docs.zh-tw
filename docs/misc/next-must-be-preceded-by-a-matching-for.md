---
title: "&#39;Next&#39; 之前必須搭配相對應的 &#39;For&#39; | Microsoft Docs"
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
  - "vbc30092"
  - "bc30092"
helpviewer_keywords: 
  - "BC30092"
ms.assetid: 4bf49bb2-c69b-443d-aa58-cb40fcfb1370
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; 之前必須搭配相對應的 &#39;For&#39;
`Next` 陳述式沒有相對應的 `For` 或 `For Each` 陳述式。`Next` 之前必須搭配相對應的 `For` 或 `For Each` 陳述式。  
  
 **錯誤 ID︰**BC30092  
  
### 更正這個錯誤  
  
1.  如果這個 `For` 迴圈是一組巢狀 `For` 迴圈的一部分，請確定已正確地終止每個迴圈。  
  
2.  請確認已正確地終止 `For` 迴圈內的其他控制結構。  
  
3.  請確定已正確地格式化這個 `For` 迴圈。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [For Each...Next 陳述式](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)