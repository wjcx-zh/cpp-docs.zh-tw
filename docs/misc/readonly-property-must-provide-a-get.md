---
title: "&#39;ReadOnly&#39; 屬性必須提供 &#39;Get&#39; | Microsoft Docs"
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
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; 屬性必須提供 &#39;Get&#39;
如果屬性宣告為 `ReadOnly`，則必須提供讀取其值的程序。  
  
 **錯誤 ID︰**BC30126  
  
### 更正這個錯誤  
  
1.  確定您在 `Property` 陳述式和 `End Property` 陳述式之間包含 `Get` 程序。  
  
2.  請確認已正確地終止 `Property` 宣告內的其他程序。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Get Statement](../Topic/Get%20Statement.md)