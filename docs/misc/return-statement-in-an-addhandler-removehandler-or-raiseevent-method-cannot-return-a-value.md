---
title: "&#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 方法中的 &#39;Return&#39; 陳述式無法傳回值 | Microsoft Docs"
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
  - "bc30940"
  - "vbc30940"
helpviewer_keywords: 
  - "BC30940"
ms.assetid: 0e4d037a-2d20-40e4-8ead-6d709d1c9c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 方法中的 &#39;Return&#39; 陳述式無法傳回值
`Custom Event` 宣告中的 `AddHandler`、`RemoveHandler` 和 `RaiseEvent` 方法可以包含 `Return` 陳述式來結束方法。 不過，`Return` 陳述式無法指定傳回值，因為方法無法傳回值。  
  
 **錯誤 ID︰**BC30940  
  
### 更正這個錯誤  
  
-   請移除 `Return` 陳述式後面的運算式。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return Statement](../Topic/Return%20Statement%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)