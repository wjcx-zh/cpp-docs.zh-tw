---
title: "&#39;Next&#39; 陳述式命名超過符合 &#39;For&#39; 陳述式的變數 | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; 陳述式命名超過符合 &#39;For&#39; 陳述式的變數
巢狀迴圈因為單一 `Next` 陳述式終止，該陳述式指定比巢狀迴圈多的迴圈變數，如下列範例中所示：  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **錯誤 ID︰**BC32037  
  
### 更正這個錯誤  
  
1.  請確定 `Next` 陳述式以迴圈起始相反的順序，指定所有巢狀迴圈變數。  
  
2.  請從 `Next` 陳述式移除所有多餘的變數。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)