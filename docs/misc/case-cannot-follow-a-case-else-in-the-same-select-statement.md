---
title: "在相同的 &#39;Select&#39; 陳述式中，&#39;Case&#39; 不可以跟隨在 &#39;Case Else&#39; 之後 | Microsoft Docs"
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
  - "bc30321"
  - "vbc30321"
helpviewer_keywords: 
  - "BC30321"
ms.assetid: eeedbceb-2c8d-4acb-b84c-8b42c058f083
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在相同的 &#39;Select&#39; 陳述式中，&#39;Case&#39; 不可以跟隨在 &#39;Case Else&#39; 之後
如果沒有找到初始 `Case` 的相符項，`Case Else` 陳述式導致執行陳述式。 在同一個 `Select` 區塊的 `Case Else` 之後找到 `Case` 陳述式。  
  
 **錯誤 ID︰**BC30321  
  
### 更正這個錯誤  
  
-   請將 `Case Else` 移至 `Case` 陳述式之後的適當位置。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)