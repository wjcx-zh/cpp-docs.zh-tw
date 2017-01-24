---
title: "&#39;GoTo &lt;標籤名稱&gt;&#39; 無效，因為 &#39;&lt;標籤名稱&gt;&#39; 位於不包含這個陳述式的 &#39;With&#39; 陳述式內部 | Microsoft Docs"
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
  - "bc30756"
  - "vbc30756"
helpviewer_keywords: 
  - "BC30756"
ms.assetid: 9c39d4ad-0b9b-45e9-b6c2-d983144b5b23
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;標籤名稱&gt;&#39; 無效，因為 &#39;&lt;標籤名稱&gt;&#39; 位於不包含這個陳述式的 &#39;With&#39; 陳述式內部
`GoTo` 陳述式只能在目前的程式碼區塊內跳躍。  
  
 **錯誤 ID︰**BC30756  
  
### 更正這個錯誤  
  
-   請重建您的程式碼，讓 `GoTo` 陳述式和標籤都位在 `With` 區塊內。  
  
## 請參閱  
 [GoTo Statement](../Topic/GoTo%20Statement.md)