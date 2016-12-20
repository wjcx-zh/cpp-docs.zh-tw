---
title: "&#39;With&#39; 之後必須搭配相對應的 &#39;End With&#39; | Microsoft Docs"
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
  - "bc30085"
  - "vbc30085"
helpviewer_keywords: 
  - "BC30085"
ms.assetid: aa88f4d0-be5f-4efe-a4ef-80e6d6124e6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;With&#39; 之後必須搭配相對應的 &#39;End With&#39;
`With` 陳述式沒有相對應的 `End With` 陳述式。 必須使用 `End With` 陳述式來結束 `With` 區塊。  
  
 **錯誤識別碼：**BC30085  
  
### 更正這個錯誤  
  
-   如果這個 `With` 區塊是一組巢狀 `With` 區塊的一部分，請確定已正確地終止每個區塊。  
  
-   將 `End With` 陳述式加入 `With` 區塊的結尾。  
  
## 請參閱  
 [With...End With Statement](../Topic/With...End%20With%20Statement%20\(Visual%20Basic\).md)