---
title: "&#39;RaiseEvent&#39; 方法必須與包含事件的委派類型 &#39;&lt;簽章&gt;&#39; 擁有相同的簽章 | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;RaiseEvent&#39; 方法必須與包含事件的委派類型 &#39;&lt;簽章&gt;&#39; 擁有相同的簽章
`Custom Event` 宣告之 `RaiseEvent` 宣告的簽章必須與自訂事件之 `As` 子句所指定的委派類型相同。  
  
 為了讓簽章相符，`RaiseEvent` 宣告和委派必須有一些參數，而且必須符合參數類型。  
  
 **錯誤 ID︰**BC31137  
  
### 更正這個錯誤  
  
-   請變更 `RaiseEvent` 宣告的參數，以符合委派類型的參數。  
  
## 範例  
 這個範例示範具有 `RaiseEvent` 宣告之正確參數類型的自訂事件。  
  
 [!code-vb[VbVbalrEventError#2](../misc/codesnippet/VisualBasic/raiseevent-method-must-have-the-same-signature-as-the-containing-event-s-delegate-type-signature_1.vb)]  
  
## 請參閱  
 [Event Statement](../Topic/Event%20Statement.md)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-tw/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)