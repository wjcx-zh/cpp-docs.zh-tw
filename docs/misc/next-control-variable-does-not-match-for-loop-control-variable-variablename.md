---
title: "Next 控制變數與 For 迴圈控制變數 &#39;&lt;變數名稱&gt;&#39; 不相符。 | Microsoft Docs"
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
  - "vbc30070"
  - "bc30070"
helpviewer_keywords: 
  - "BC30070"
ms.assetid: e9e96008-b053-4fa0-8966-decaad99fecd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Next 控制變數與 For 迴圈控制變數 &#39;&lt;變數名稱&gt;&#39; 不相符。
`For...Next` 迴圈之 `Next` 陳述式中的控制變數必須符合對應 `For` 陳述式中的變數。  
  
 **錯誤 ID︰**BC30070  
  
### 更正這個錯誤  
  
1.  請檢查 `Next` 陳述式與對應 `For` 陳述式中的變數拼字，確定相符。  
  
2.  請確定沒有不小心刪除封閉式迴圈的任何部分。  
  
3.  如果這個迴圈是一組巢狀迴圈的一部分，請確定已正確地終止每個迴圈。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)