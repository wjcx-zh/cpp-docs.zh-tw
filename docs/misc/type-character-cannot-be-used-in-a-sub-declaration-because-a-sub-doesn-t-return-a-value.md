---
title: "由於 &#39;Sub&#39; 不會傳回值，類型字元不可以在 &#39;Sub&#39; 宣告中使用 | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 由於 &#39;Sub&#39; 不會傳回值，類型字元不可以在 &#39;Sub&#39; 宣告中使用
如同 `Function` 程序，`Sub` 程序是可接受引數並執行一系列陳述式的個別程序。 但不同於 `Function` 程序，`Sub` 沒有傳回值，因此無法包含類型宣告。  
  
 **錯誤 ID︰**BC30303  
  
### 更正這個錯誤  
  
-   將 `Sub` 程序變更為 `Function` 程序。  
  
## 請參閱  
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [函式程序](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)