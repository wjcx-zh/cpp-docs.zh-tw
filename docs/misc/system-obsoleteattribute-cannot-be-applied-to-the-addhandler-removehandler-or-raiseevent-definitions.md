---
title: "&#39;System.ObsoleteAttribute&#39; 無法套用至 &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 定義 | Microsoft Docs"
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
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.ObsoleteAttribute&#39; 無法套用至 &#39;AddHandler&#39;、&#39;RemoveHandler&#39; 或 &#39;RaiseEvent&#39; 定義
'System.ObsoleteAttribute' 無法套用至 'AddHandler'、'RemoveHandler' 或 'RaiseEvent' 定義。 必要時，請將屬性直接套用至事件。  
  
 自訂事件會將 <xref:System.ObsoleteAttribute> 套用至其 `AddHandler`、`RemoveHandler` 或 `RaiseEvent` 程序。  
  
 <xref:System.ObsoleteAttribute> 會將程式設計項目標記為不再使用，並通知使用者未來的產品版本會移除該項目。  
  
 使用自訂事件的某些部分而不使用其他部分是毫無意義的。  
  
 **錯誤 ID：**BC31142  
  
### 更正這個錯誤  
  
-   從個別的程序宣告中移除 <xref:System.ObsoleteAttribute>，並將它套用至整個事件宣告。  
  
## 請參閱  
 <xref:System.ObsoleteAttribute>   
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler Statement](../Topic/AddHandler%20Statement.md)   
 [RemoveHandler Statement](../Topic/RemoveHandler%20Statement.md)   
 [RaiseEvent Statement](../Topic/RaiseEvent%20Statement.md)