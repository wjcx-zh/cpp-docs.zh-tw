---
title: "&#39;&lt;規範&gt;&#39; 在介面事件宣告中無效 | Microsoft Docs"
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
  - "bc30275"
  - "vbc30275"
helpviewer_keywords: 
  - "BC30275"
ms.assetid: bd12c952-c619-4753-8d6d-90ef4086fdc2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;規範&gt;&#39; 在介面事件宣告中無效
介面內的 `Event` 陳述式包含不允許的關鍵字 \(例如 `Implements`\)。 介面只會定義成員，無法實作它們。  
  
 **錯誤 ID︰**BC30275  
  
### 更正這個錯誤  
  
1.  請從宣告陳述式中移除關鍵字。  
  
2.  請將介面成員實作移至實作介面的類別。  
  
## 請參閱  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)