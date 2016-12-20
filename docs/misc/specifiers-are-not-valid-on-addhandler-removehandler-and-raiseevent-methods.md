---
title: "&#39;AddHandler&#39;、&#39;RemoveHandler&#39; 和 &#39;RaiseEvent&#39; 方法上的規範無效 | Microsoft Docs"
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
  - "vbc31135"
  - "bc31135"
helpviewer_keywords: 
  - "BC31135"
ms.assetid: 2eaf5a6f-d201-4f9b-bcdf-12170cb44791
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 和 &#39;RaiseEvent&#39; 方法上的規範無效
`AddHandler`、`RemoveHandler` 和 `RaiseEvent` 方法宣告無法以 `Public` 或 `ReadOnly` 等關鍵字修改。 只有可修改的宣告才能包含這類關鍵字。  
  
 **錯誤 ID︰**BC31135  
  
### 更正這個錯誤  
  
-   從方法宣告中移除關鍵字。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [NIB 關鍵字 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/3a6fda51-6ade-4862-a407-1c305c3906ec)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)