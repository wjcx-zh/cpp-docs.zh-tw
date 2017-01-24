---
title: "&#39;ReDim&#39; 陳述式需要每個陣列維度新界限的括弧清單 | Microsoft Docs"
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
  - "bc30670"
  - "vbc30670"
helpviewer_keywords: 
  - "BC30670"
ms.assetid: b2c5fea3-e7db-4797-b917-d61a65befbd4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; 陳述式需要每個陣列維度新界限的括弧清單
您必須在 `ReDim` 陳述式中指定陣列的新大小。  
  
 **錯誤 ID：**BC30670  
  
### 更正這個錯誤  
  
-   提供陣列的每個陣序大小；例如：  
  
    ```  
    ReDim arr(5, 6)  
    ```  
  
## 請參閱  
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)