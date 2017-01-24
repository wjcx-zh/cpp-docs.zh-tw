---
title: "&#39;ElseIf&#39; 之前必須搭配相對應的 &#39;If&#39; 或 &#39;ElseIf&#39; | Microsoft Docs"
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
  - "bc36005"
  - "vbc36005"
helpviewer_keywords: 
  - "BC36005"
ms.assetid: bcebae85-b438-4839-bada-2f8f8dcc8a86
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ElseIf&#39; 之前必須搭配相對應的 &#39;If&#39; 或 &#39;ElseIf&#39;
`ElseIf` 陳述式沒有相對應的 `If` 陳述式。`ElseIf` 之前必須搭配 `If` 陳述式或另一個 `ElseIf` 陳述式。  
  
 **錯誤 ID︰**BC36005  
  
### 更正這個錯誤  
  
1.  如果這個 `If` 區塊是一組巢狀控制結構的一部分，請確定已正確地終止每個結構。  
  
2.  請確認已正確地終止 `If` 區塊內的其他巢狀控制結構。  
  
3.  請確定已正確地格式化這個 `If` 區塊。  
  
## 請參閱  
 [If...Then...Else Statement](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)   
 [Decision Structures](../Topic/Decision%20Structures%20\(Visual%20Basic\).md)