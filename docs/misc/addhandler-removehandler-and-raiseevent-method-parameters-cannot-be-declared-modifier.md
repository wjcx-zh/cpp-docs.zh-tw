---
title: "&#39;AddHandler&#39;、&#39;RemoveHandler&#39; 和 &#39;RaiseEvent&#39; 方法參數不可以宣告為 &#39;&lt;修飾詞&gt;&#39; | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 和 &#39;RaiseEvent&#39; 方法參數不可以宣告為 &#39;&lt;修飾詞&gt;&#39;
不能使用 `Optional` 或 `ParamArray` 修飾詞來宣告 `AddHandler`、`RemoveHandler` 和 `RaiseEvent` 方法的參數。  
  
 `Optional` 或 `ParamArray` 修飾詞僅允許用在 `Declare`、`Function`、`Property` 和 `Sub` 宣告的參數上。  
  
 **錯誤 ID︰**BC31138  
  
### 更正這個錯誤  
  
-   請從參數清單中移除 `Optional` 或 `ParamArray` 關鍵字。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Optional](../Topic/Optional%20\(Visual%20Basic\).md)   
 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)