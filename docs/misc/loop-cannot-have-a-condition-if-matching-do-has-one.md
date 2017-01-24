---
title: "如果相對應的 &#39;Do&#39; 有條件，&#39;Loop&#39; 就不可以有條件 | Microsoft Docs"
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
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如果相對應的 &#39;Do&#39; 有條件，&#39;Loop&#39; 就不可以有條件
`Loop` 陳述式包含 `While` 或 `Until` 子句，而對應的 `Do` 陳述式也包含這類子句。 在迴圈中的 `Do` 和 `Loop` 陳述式只有其中一個可以指定條件。  
  
 **錯誤 ID︰**BC30238  
  
### 更正這個錯誤  
  
-   請從 `Do` 陳述式或 `Loop` 陳述式移除 `While` 或 `Until` 子句。  
  
## 請參閱  
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)