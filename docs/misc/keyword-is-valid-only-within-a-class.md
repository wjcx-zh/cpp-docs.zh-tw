---
title: "&#39;&lt;關鍵字&gt;&#39; 只在類別中有效 | Microsoft Docs"
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
  - "bc32002"
  - "vbc32002"
helpviewer_keywords: 
  - "BC32002"
ms.assetid: 773d8d50-abb8-4257-83a5-6e017c199d82
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;關鍵字&gt;&#39; 只在類別中有效
與類別相關的關鍵字 \(例如 `Me` 或 `MyClass`\) 用在類別定義外部。  
  
 **錯誤 ID︰**BC32002  
  
### 更正這個錯誤  
  
-   如果使用關鍵字的程式碼牽涉到類別執行個體，請將它移至類別實作。  
  
-   如果使用關鍵字的程式碼未套用至類別，請移除無效的關鍵字。  
  
## 請參閱  
 [我](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- delete](http://msdn.microsoft.com/zh-tw/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)