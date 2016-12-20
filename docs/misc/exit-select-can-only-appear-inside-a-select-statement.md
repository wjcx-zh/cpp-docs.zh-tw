---
title: "&#39;Exit Select&#39; 只可以在 &#39;Select&#39; 陳述式中出現 | Microsoft Docs"
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
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Select&#39; 只可以在 &#39;Select&#39; 陳述式中出現
`Exit Select` 陳述式出現在 `Select` 區塊外。`Exit Select` 僅適用於 `Select` 或 `Select Case` 陳述式與其相對應的 `End Select` 陳述式之間。  
  
 **錯誤 ID︰**BC30099  
  
### 更正這個錯誤  
  
1.  請確定有效的 `Select` 或 `Select Case` 陳述式出現在 `Exit Select` 前面，而它的後面出現有效的 `End Select` 陳述式。  
  
2.  請確認已正確地終止 `Select` 區塊內的其他控制結構。  
  
## 請參閱  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)