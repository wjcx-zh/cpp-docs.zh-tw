---
title: "&lt;錯誤&gt;：&#39;&lt;類別名稱1&gt;&#39; 繼承自 &#39;&lt;類別名稱2&gt;&#39; | Microsoft Docs"
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
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;錯誤&gt;：&#39;&lt;類別名稱1&gt;&#39; 繼承自 &#39;&lt;類別名稱2&gt;&#39;
偵測到循環繼承階層架構。 類別指定為繼承自本身，或繼承自另一個直接或最終繼承自它的另一個類別。  
  
 這個訊息可能會出現多次，以追蹤循環繼承路徑。  
  
 **錯誤 ID︰**BC30256  
  
### 更正這個錯誤  
  
-   請藉由移除循環繼承路徑中的至少一個 `Inherits` 陳述式來中斷循環。  
  
## 請參閱  
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)