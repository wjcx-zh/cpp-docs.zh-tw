---
title: "&#39;Exit Do&#39; 只可以在 &#39;Do&#39; 陳述式中出現 | Microsoft Docs"
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
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Do&#39; 只可以在 &#39;Do&#39; 陳述式中出現
`Exit Do` 陳述式出現在 `Do` 迴圈外。`Exit Do` 僅適用於 `Do` 陳述式與其相對應的 `Loop` 陳述式之間。  
  
 **錯誤 ID︰**BC30089  
  
### 更正這個錯誤  
  
1.  請確定有效的 `Do` 陳述式出現在 `Exit Do` 前面，而它的後面出現有效的 `Loop` 陳述式。  
  
2.  請確認已正確地終止 `Do` 迴圈內的其他控制結構。  
  
## 請參閱  
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)