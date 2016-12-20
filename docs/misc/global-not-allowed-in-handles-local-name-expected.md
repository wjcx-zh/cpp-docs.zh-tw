---
title: "控制代碼中不允許 &#39;Global&#39;; 必須是區域名稱 | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 控制代碼中不允許 &#39;Global&#39;; 必須是區域名稱
`Handles` 子句必須參考本機的事件。`Global` 關鍵字可提供對通用程式設計項目的存取。  
  
 **錯誤 ID︰**BC36002  
  
### 更正這個錯誤  
  
-   請變更 `Handles` 子句以參考事件的本機執行個體，而不要參考全域執行個體。  
  
## 請參閱  
 [Global \- delete](http://msdn.microsoft.com/zh-tw/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)