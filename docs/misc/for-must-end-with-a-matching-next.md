---
title: "&#39;For&#39; 之後必須搭配相對應的 &#39;Next&#39; | Microsoft Docs"
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
  - "vbc30084"
  - "bc30084"
helpviewer_keywords: 
  - "BC30084"
ms.assetid: 4c5e49c2-7343-4487-b5f8-a38c97ba895b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For&#39; 之後必須搭配相對應的 &#39;Next&#39;
`For` 陳述式沒有相對應的 `Next` 陳述式。 必須使用 `Next` 陳述式來結束 `For` 迴圈。  
  
 **錯誤 ID︰**BC30084  
  
### 更正這個錯誤  
  
-   如果這個 `For` 迴圈是一組巢狀迴圈的一部分，請確定已正確地終止每個迴圈。  
  
-   將 `Next` 陳述式加入 `For` 迴圈的結尾。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)