---
title: "&#39;Exit While&#39; 只可以在 &#39;While&#39; 陳述式中出現 | Microsoft Docs"
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
  - "vbc30097"
  - "bc30097"
helpviewer_keywords: 
  - "BC30097"
ms.assetid: cf0a3e09-5252-4198-bb27-c103c98d9f19
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit While&#39; 只可以在 &#39;While&#39; 陳述式中出現
`Exit While` 陳述式出現在 `While` 區塊外。`Exit While` 僅適用於 `While` 陳述式與其相對應的 `End While` 陳述式之間。  
  
 **錯誤 ID︰**BC30097  
  
### 更正這個錯誤  
  
1.  請確定有效的 `While` 陳述式出現在 `Exit While` 前面，而它的後面出現有效的 `End While` 陳述式。  
  
2.  請確認已正確地終止 `While` 區塊內的其他控制結構。  
  
## 請參閱  
 [While...End While Statement](../Topic/While...End%20While%20Statement%20\(Visual%20Basic\).md)