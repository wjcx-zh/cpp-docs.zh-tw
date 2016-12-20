---
title: "&#39;AddHandler&#39; 和 &#39;RemoveHandler&#39; 方法參數不可以宣告為 &#39;ByRef&#39; | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39; 和 &#39;RemoveHandler&#39; 方法參數不可以宣告為 &#39;ByRef&#39;
不能使用 `ByRef` 修飾詞來宣告 `AddHandler` 和 `RemoveHandler` 方法的參數。  
  
 **錯誤 ID︰**BC31134  
  
### 更正這個錯誤  
  
-   請從參數中移除 `ByRef` 關鍵字。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)