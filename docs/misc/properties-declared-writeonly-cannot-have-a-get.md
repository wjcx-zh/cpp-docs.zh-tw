---
title: "宣告為 &#39;WriteOnly&#39; 的屬性無法擁有 &#39;Get&#39; | Microsoft Docs"
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
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 宣告為 &#39;WriteOnly&#39; 的屬性無法擁有 &#39;Get&#39;
`Get` 程序會讀取屬性值。 無法讀取 `WriteOnly` 屬性。  
  
 **錯誤 ID：**BC30023  
  
### 更正這個錯誤  
  
-   請從 `Property` 陳述式中移除 `WriteOnly` 關鍵字，或從屬性主體中移除 `Get` 程序。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Get Statement](../Topic/Get%20Statement.md)   
 [WriteOnly](../Topic/WriteOnly%20\(Visual%20Basic\).md)