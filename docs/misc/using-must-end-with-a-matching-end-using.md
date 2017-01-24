---
title: "&#39;Using&#39; 之後必須搭配相對應的 &#39;End Using&#39; | Microsoft Docs"
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
  - "vbc36008"
  - "bc36008"
helpviewer_keywords: 
  - "BC36008"
ms.assetid: 83269108-b169-40a6-bbcc-af1ac8fcfd67
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Using&#39; 之後必須搭配相對應的 &#39;End Using&#39;
`Using` 陳述式沒有相對應的 `End Using` 陳述式。  
  
 必須使用 `End Using` 陳述式來結束 `Using` 區塊。  
  
 **錯誤 ID︰**BC36008  
  
### 更正這個錯誤  
  
1.  如果這個 `Using` 區塊是一組巢狀 `Using` 區塊的一部分，請確定已正確地終止每個區塊。  
  
2.  將 `End Using` 陳述式加入 `Using` 區塊的結尾。  
  
## 請參閱  
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)