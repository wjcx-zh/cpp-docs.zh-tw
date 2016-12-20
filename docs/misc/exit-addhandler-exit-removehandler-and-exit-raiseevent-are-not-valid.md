---
title: "&#39;Exit AddHandler&#39;、&#39;Exit RemoveHandler&#39; 和 &#39;Exit RaiseEvent&#39; 無效 | Microsoft Docs"
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
  - "vbc31111"
  - "bc31111"
helpviewer_keywords: 
  - "BC31111"
ms.assetid: e02264f3-0645-4de5-b622-8a2a74496b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit AddHandler&#39;、&#39;Exit RemoveHandler&#39; 和 &#39;Exit RaiseEvent&#39; 無效
'Exit AddHandler'、'Exit RemoveHandler' 和 'Exit RaiseEvent' 無效。 請使用 'Return' 結束事件成員。  
  
 `Exit` 陳述式無法用來結束 `Custom Event` 宣告中的 `AddHandler`、`RemoveHandler` 或 `RaiseEvent` 方法。 請改用未指定傳回運算式的 `Return` 陳述式來結束這個方法。  
  
 **錯誤 ID︰**BC31111  
  
### 更正這個錯誤  
  
-   以 `Return` 陳述式取代 `Exit` 陳述式。  
  
     確定 `Return` 陳述式未指定傳回運算式。  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return Statement](../Topic/Return%20Statement%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)