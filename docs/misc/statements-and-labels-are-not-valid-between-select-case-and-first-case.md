---
title: "在 &#39;Select Case&#39; 與第一個 &#39;Case&#39; 間，不可以使用陳述式和標籤 | Microsoft Docs"
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
  - "bc30058"
  - "vbc30058"
helpviewer_keywords: 
  - "BC30058"
ms.assetid: 399b4659-f7df-4377-80be-43019f1e6206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 &#39;Select Case&#39; 與第一個 &#39;Case&#39; 間，不可以使用陳述式和標籤
不是註解的陳述式出現在開頭 `Select` 或 `Select Case` 陳述式與其第一個 `Case` 陳述式之間。  
  
 **錯誤 ID︰**BC30058  
  
### 更正這個錯誤  
  
-   如果介入陳述式是註解，則前面會加上註解分隔符號 \(`'` 或 `REM`\)。 否則，請移動或刪除陳述式。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)