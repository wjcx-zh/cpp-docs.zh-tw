---
title: "&#39;&lt;類別名稱1&gt;&#39; 無法從 &lt;類型&gt; &#39;&lt;類別名稱2&gt;&#39; 繼承，因為 &#39;&lt;類別名稱2&gt;&#39; 被宣告為 &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc30299"
  - "bc30299"
helpviewer_keywords: 
  - "BC30299"
ms.assetid: 627d50f5-9e75-495d-93f7-50096ba2ea08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類別名稱1&gt;&#39; 無法從 &lt;類型&gt; &#39;&lt;類別名稱2&gt;&#39; 繼承，因為 &#39;&lt;類別名稱2&gt;&#39; 被宣告為 &#39;NotInheritable&#39;
類別嘗試從另一個類別繼承，但所需的基底類別已指定為 `NotInheritable`。`NotInheritable` 類別主要是用來防止意外衍生。  
  
 **錯誤 ID︰**BC30299  
  
### 更正這個錯誤  
  
-   從所需基底類別定義中移除 `NotInheritable` 關鍵字，或移除 `Inherits` 陳述式。  
  
## 請參閱  
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)