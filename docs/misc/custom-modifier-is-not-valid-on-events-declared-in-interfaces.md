---
title: "&#39;Custom&#39; 修飾詞在以介面宣告的事件中無效 | Microsoft Docs"
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
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Custom&#39; 修飾詞在以介面宣告的事件中無效
無法在介面中宣告自訂事件，因為自訂事件必須提供其 `AddHandler`、`RemoverHandler` 和 `RaiseEvent` 方法的實作。  
  
 `Custom` 關鍵字可用於實作事件的衍生類別。  
  
 **錯誤 ID︰**BC31121  
  
### 更正這個錯誤  
  
-   從介面的事件宣告中移除 `Custom` 關鍵字。  
  
## 範例  
 這個範例示範如何將介面中宣告的事件實作為自訂事件。  
  
 [!code-vb[VbVbalrEventError#3](../misc/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-in-interfaces_1.vb)]  
  
## 請參閱  
 [Custom \- delete](http://msdn.microsoft.com/zh-tw/dc62be07-c896-4866-a533-982a661d143f)   
 [Event Statement](../Topic/Event%20Statement.md)   
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)