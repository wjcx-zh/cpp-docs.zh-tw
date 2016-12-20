---
title: "&#39;Continue For&#39; 只可以在 &#39;For&#39; 陳述式中出現 | Microsoft Docs"
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
  - "bc30783"
  - "vbc30783"
helpviewer_keywords: 
  - "BC30783"
ms.assetid: 70891018-27c8-4d36-b168-8cc7177d70cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue For&#39; 只可以在 &#39;For&#39; 陳述式中出現
`Continue For` 陳述式只可以在 `For...Next` 迴圈內出現。  
  
 **錯誤 ID︰**BC30783  
  
### 更正這個錯誤  
  
1.  如果 `Continue For` 陳述式是在 `Do...Loop` 中，請將陳述式變更為 `Continue Do`。  
  
     \-或\-  
  
     如果 `Continue For` 陳述式是在 `While...End While` 迴圈內，請將陳述式變更為 `Continue While`。  
  
2.  否則，請移除 `Continue For` 陳述式。  
  
## 請參閱  
 [Continue Statement](../Topic/Continue%20Statement%20\(Visual%20Basic\).md)   
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)