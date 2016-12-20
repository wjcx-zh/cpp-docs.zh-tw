---
title: "&#39;Case Else&#39; 只能在 &#39;Select Case&#39; 陳述式內出現 | Microsoft Docs"
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
  - "bc30071"
  - "vbc30071"
helpviewer_keywords: 
  - "BC30071"
ms.assetid: 9a4f8ccb-717a-4d18-91b4-4a373202c38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case Else&#39; 只能在 &#39;Select Case&#39; 陳述式內出現
`Case Else` 陳述式出現在 `Select` 區塊外。`Case Else` 陳述式只能用在 `Select` 或 `Select Case` 陳述式和其相對應的 `End Select` 陳述式之間。  
  
 **錯誤 ID：**BC30071  
  
### 更正這個錯誤  
  
-   移除 `Case Else` 陳述式或將它移至 `Select` 區塊內。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)