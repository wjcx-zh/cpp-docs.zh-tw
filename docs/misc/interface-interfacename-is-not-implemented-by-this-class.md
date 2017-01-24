---
title: "介面 &#39;&lt;介面名稱&gt;&#39; 尚未由此類別實作 | Microsoft Docs"
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
  - "bc31035"
  - "vbc31035"
helpviewer_keywords: 
  - "BC31035"
ms.assetid: 99ddabb5-20e0-4cf6-a8d4-1ca91f3c7511
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 介面 &#39;&lt;介面名稱&gt;&#39; 尚未由此類別實作
這個類別或結構的成員嘗試實作的成員，是類別或結構不會實作之介面的成員。  
  
 **錯誤 ID：**BC31035  
  
### 更正這個錯誤  
  
-   將 `Implements` 陳述式加入類別或結構開頭，使其實作適當的介面。  
  
-   從導致此錯誤的成員中，移除 `Implements` 關鍵字。  
  
## 請參閱  
 [Interfaces](../Topic/Interfaces%20\(Visual%20Basic\).md)   
 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)