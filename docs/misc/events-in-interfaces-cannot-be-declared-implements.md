---
title: "介面中的事件無法宣告為 &#39;&lt;實作&gt;&#39; | Microsoft Docs"
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
  - "bc30688"
  - "vbc30688"
helpviewer_keywords: 
  - "BC30688"
ms.assetid: 577823c1-815c-4f1c-9177-4bbf73fa92db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 介面中的事件無法宣告為 &#39;&lt;實作&gt;&#39;
在介面中宣告的事件不能實作其他介面的事件。  
  
 **錯誤識別碼：**BC30688  
  
### 更正這個錯誤  
  
1.  請移除 `Implements` 陳述式。  
  
2.  實作類別或結構中的事件。  
  
## 請參閱  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)