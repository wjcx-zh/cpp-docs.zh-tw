---
title: "&#39;Case&#39; 只能出現在 &#39;Select Case&#39; 陳述式 | Microsoft Docs"
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
  - "vbc30072"
  - "bc30072"
helpviewer_keywords: 
  - "BC30072"
ms.assetid: da808bc3-f154-444a-b547-3cf55beff8a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; 只能出現在 &#39;Select Case&#39; 陳述式
`Case` 陳述式出現在 `Select` 區塊外。`Case` 陳述式只能用在 `Select` 或 `Select Case` 陳述式和其相對應的 `End Select` 陳述式之間。  
  
 **錯誤識別碼：**BC30072  
  
### 更正這個錯誤  
  
-   移除 `Case` 陳述式或將它移至 `Select` 區塊內。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)