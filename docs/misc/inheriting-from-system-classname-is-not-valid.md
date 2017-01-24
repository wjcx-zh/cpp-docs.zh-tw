---
title: "從 &#39;System.&lt;類別名稱&gt;&#39; 繼承無效 | Microsoft Docs"
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
  - "vbc30015"
  - "bc30015"
helpviewer_keywords: 
  - "BC30015"
ms.assetid: b4c005df-a510-47c7-b5cc-27f4514d32b6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 從 &#39;System.&lt;類別名稱&gt;&#39; 繼承無效
類別不可從 `System.Array`、`System.Delegate`、`System.Enum` 或 `System.ValueType` 繼承。  
  
 **錯誤 ID︰**BC30015  
  
### 更正這個錯誤  
  
-   移除 `Inherits` 陳述式，或將其變更為繼承自有效的基底類別。  
  
## 請參閱  
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [Object Variable Declaration](../Topic/Object%20Variable%20Declaration%20\(Visual%20Basic\).md)