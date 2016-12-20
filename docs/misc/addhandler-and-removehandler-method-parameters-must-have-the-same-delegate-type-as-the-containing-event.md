---
title: "&#39;AddHandler&#39; 和 &#39;RemoveHandler&#39; 方法參數必須與包含事件擁有相同的委派類型 | Microsoft Docs"
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
  - "bc31136"
  - "vbc31136"
helpviewer_keywords: 
  - "BC31136"
ms.assetid: 199b2f7b-a85e-465d-9853-0995156e7ab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39; 和 &#39;RemoveHandler&#39; 方法參數必須與包含事件擁有相同的委派類型
`Custom Event` 宣告必須有 `AddHandler` 或 `RemoveHandler` 宣告，每個宣告會接受自訂事件的 `As` 子句所指定之委派類型的單一參數。  
  
 **錯誤 ID︰**BC31136  
  
### 更正這個錯誤  
  
-   請變更參數類型，讓它與自訂事件之 `As` 子句所指定的委派類型相同。  
  
## 範例  
 這個範例示範具有 `AddHandler` 和 `RemoveHandler` 宣告之正確參數類型的自訂事件。  
  
 [!code-vb[VbVbalrEventError#1](../misc/codesnippet/VisualBasic/addhandler-and-removehandler-method-parameters-must-have-the-same-delegate-type-as-the-containing-event_1.vb)]  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/zh-tw/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/zh-tw/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)