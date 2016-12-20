---
title: "無法建立模組 &#39;&lt;模組名稱&gt;&#39; 的執行個體 | Microsoft Docs"
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
  - "bc30166"
  - "vbc30166"
helpviewer_keywords: 
  - "BC30166"
ms.assetid: 40b9dbd3-9b57-450f-a631-b0ab06ca19c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法建立模組 &#39;&lt;模組名稱&gt;&#39; 的執行個體
模組僅能作為單一共用執行個體，因此無法建立額外的執行個體。  
  
 **錯誤 ID︰**BC30166  
  
### 更正這個錯誤  
  
-   將模組變更為類別，或將 `New` 子句中的模組取代為類別名稱。  
  
## 請參閱  
 [Module Statement](../Topic/Module%20Statement.md)   
 [不在組建中：Implements 關鍵字和 Implements 陳述式](http://msdn.microsoft.com/zh-tw/b96560f7-6413-480f-a1e2-f80253bab5be)