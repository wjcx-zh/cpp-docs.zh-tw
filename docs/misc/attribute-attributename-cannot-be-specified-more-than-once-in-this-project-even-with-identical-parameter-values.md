---
title: "屬性 &#39;&lt;屬性名稱&gt;&#39; 在這個專案中不可以重複指定，即使是使用相同的參數值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性 &#39;&lt;屬性名稱&gt;&#39; 在這個專案中不可以重複指定，即使是使用相同的參數值
自訂屬性在相同的程式設計項目上指定多次，但是 <xref:System.AttributeUsageAttribute> 已套用至自訂屬性，且其 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 屬性設定為 `False`。<xref:System.AttributeUsageAttribute.AllowMultiple%2A> 控制屬性是否為多重用途。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC41000  
  
### 更正這個錯誤  
  
-   請移除自訂屬性的額外指定，或在套用到它的 <xref:System.AttributeUsageAttribute> 中，將 <xref:System.AttributeUsageAttribute.AllowMultiple%2A> 設為 `True`。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)