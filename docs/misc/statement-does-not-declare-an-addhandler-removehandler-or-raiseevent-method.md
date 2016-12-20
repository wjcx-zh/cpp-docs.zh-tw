---
title: "陳述式沒有宣告 &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 方法 | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陳述式沒有宣告 &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 方法
陳述式未在 `Custom Event` 程序前後提供 `AddHandler`、`RemoveHandler` 或 `RaiseEvent` 宣告陳述式。 自訂事件宣告是以 `Custom Event` 和 `End Event` 陳述式包圍的程式碼區塊。 在這個區塊內，每個 `Custom Event` 程序都會顯示為以一個宣告陳述式和一個 `End` 陳述式所包圍的內部區塊。  
  
 **錯誤 ID︰**BC31113  
  
### 更正這個錯誤  
  
-   提供 `AddHandler`、`RemoveHandler` 或 `RaiseEvent` 宣告陳述式。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)