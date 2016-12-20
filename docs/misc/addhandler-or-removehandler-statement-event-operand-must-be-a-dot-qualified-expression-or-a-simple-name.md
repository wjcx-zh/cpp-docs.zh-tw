---
title: "&#39;AddHandler&#39; 或 &#39;RemoveHandler&#39; 陳述式事件運算元必須是點限定運算式 (dot-qualified expression) 或是簡單名稱 | Microsoft Docs"
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
  - "vbc30677"
  - "bc30677"
helpviewer_keywords: 
  - "BC30677"
ms.assetid: b71eb2f0-0bb2-4aeb-94ec-5c37ab960d9e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39; 或 &#39;RemoveHandler&#39; 陳述式事件運算元必須是點限定運算式 (dot-qualified expression) 或是簡單名稱
為事件引數指定了無法辨識為事件的 `AddHandler` 或 `RemoveHandler` 項目。  
  
 **錯誤 ID：**BC30677  
  
### 更正這個錯誤  
  
-   指定引發事件的物件名稱，後面接著一個點 \(`.`\) 和事件名稱，如下列範例所示。  
  
     [!code-vb[VbVbalrEventError#30](../misc/codesnippet/VisualBasic/addhandler-or-removehandler-statement-event-operand-must-be-a-dot-qualified-expression-or-a-simple-name_1.vb)]  
  
## 請參閱  
 [AddHandler Statement](../Topic/AddHandler%20Statement.md)   
 [RemoveHandler Statement](../Topic/RemoveHandler%20Statement.md)   
 [不在組建中：AddHandler 和 RemoveHandler](http://msdn.microsoft.com/zh-tw/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)