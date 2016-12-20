---
title: "在多個基底介面都有 &#39;&lt;成員名稱&gt;&#39; | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在多個基底介面都有 &#39;&lt;成員名稱&gt;&#39;
在多個基底介面都有 '\<成員名稱\>'。 請使用在 'Implements' 子句中宣告 '\<成員名稱\>' 的介面名稱來取代衍生介面的名稱。  
  
 這個介面會從多個介面中繼承同名成員，進而產生模稜兩可。  
  
 **錯誤 ID︰**BC31040  
  
### 更正這個錯誤  
  
-   在 `Implements` 子句中使用定義介面名稱，而非衍生介面的名稱。  
  
## 請參閱  
 [Interfaces](../Topic/Interfaces%20\(Visual%20Basic\).md)   
 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)