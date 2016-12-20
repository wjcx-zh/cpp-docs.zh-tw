---
title: "&#39;WriteOnly&#39; 屬性必須提供 &#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30125"
  - "vbc30125"
helpviewer_keywords: 
  - "BC30125"
ms.assetid: c2b18086-9cd9-4094-b9a9-491c8d617096
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;WriteOnly&#39; 屬性必須提供 &#39;Set&#39;
如果屬性宣告為 `WriteOnly`，則必須提供寫入其值的程序。  
  
 **錯誤 ID︰**BC30125  
  
### 更正這個錯誤  
  
1.  確定您在 `Property` 陳述式和 `End Property` 陳述式之間包含 `Set` 程序。  
  
2.  請確認已正確地終止 `Property` 宣告內的其他程序。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)