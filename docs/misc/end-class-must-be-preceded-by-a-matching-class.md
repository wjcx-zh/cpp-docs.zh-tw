---
title: "&#39;End Class&#39; 之前必須搭配相對應的 &#39;Class&#39; | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Class&#39; 之前必須搭配相對應的 &#39;Class&#39;
`End Class` 用來完成 `Class` 區塊，因此它只能出現在區塊結尾。 您有多餘的 `End Class`，或您的 `End Class` 陳述式出現在其對應 `Class` 區塊的範圍之外。  
  
 **錯誤 ID︰**BC30460  
  
### 更正這個錯誤  
  
-   找到並移除任何多餘的 `End Class` 陳述式。  
  
-   請將 `End Class` 陳述式移至您程式碼中的適當位置。  
  
## 請參閱  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)