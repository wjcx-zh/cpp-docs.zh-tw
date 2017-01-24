---
title: "&#39;Exit For&#39; 只可以在 &#39;For&#39; 陳述式中出現 | Microsoft Docs"
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
  - "bc30096"
  - "vbc30096"
helpviewer_keywords: 
  - "BC30096"
ms.assetid: 1062a329-9364-4234-9175-4c70a51cb7ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit For&#39; 只可以在 &#39;For&#39; 陳述式中出現
`Exit For` 陳述式出現在 `For` 迴圈外。`Exit For` 僅適用於 `For` 或 `For Each` 陳述式與其相對應的 `Next` 陳述式之間。  
  
 **錯誤 ID︰**BC30096  
  
### 更正這個錯誤  
  
1.  請確定有效的 `For` 或 `For Each` 陳述式出現在 `Exit For` 前面，而它的後面出現有效的 `Next` 陳述式。  
  
2.  請確認已正確地終止 `For` 迴圈內的其他控制結構。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [For Each...Next 陳述式](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)