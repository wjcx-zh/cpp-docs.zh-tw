---
title: "&#39;Next&#39; 控制變數與 &#39;For&#39; 迴圈控制變數不相符 | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; 控制變數與 &#39;For&#39; 迴圈控制變數不相符
`For...Next` 迴圈之 `Next` 陳述式中的控制變數必須符合對應 `For` 陳述式中的變數。  
  
 **錯誤 ID︰**BC30976  
  
### 更正這個錯誤  
  
-   檢查 `Next` 陳述式與對應 `For` 陳述式中的變數拼字，確定相符。  
  
-   確定沒有不小心刪除封閉式迴圈的任何部分。  
  
-   如果這個迴圈是一組巢狀迴圈的一部分，請確定已正確地終止每個迴圈。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)