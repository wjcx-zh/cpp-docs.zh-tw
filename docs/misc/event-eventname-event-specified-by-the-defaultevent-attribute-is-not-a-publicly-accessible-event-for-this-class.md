---
title: "&#39;DefaultEvent&#39; 屬性所指定的 &#39;&lt;事件名稱&gt;&#39; 事件，對這個類別而言並非可以公開存取的事件。 | Microsoft Docs"
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
  - "vbc30770"
  - "bc30770"
helpviewer_keywords: 
  - "BC30770"
ms.assetid: 7524fba7-2a37-4bc3-b789-87d73a166575
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DefaultEvent&#39; 屬性所指定的 &#39;&lt;事件名稱&gt;&#39; 事件，對這個類別而言並非可以公開存取的事件。
<xref:System.ComponentModel.DefaultEventAttribute> 屬性必須在要套用屬性的類別中，指定可公開存取事件的名稱。  
  
 **錯誤識別碼：**BC30770  
  
### 更正這個錯誤  
  
1.  請確定類別會定義可公開存取的事件。  
  
2.  請確定類別中的事件名稱符合 <xref:System.ComponentModel.DefaultEventAttribute> 屬性指定的名稱。  
  
## 請參閱  
 <xref:System.ComponentModel.DefaultEventAttribute>   
 [Event Statement](../Topic/Event%20Statement.md)   
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)