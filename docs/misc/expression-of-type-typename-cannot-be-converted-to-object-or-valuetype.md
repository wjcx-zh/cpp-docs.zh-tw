---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 的運算式不能轉換為 &#39;Object&#39; 或 &#39;ValueType&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 的運算式不能轉換為 &#39;Object&#39; 或 &#39;ValueType&#39;
運算式評估為 Common Language Runtime \(CLR\) 無法 box 處理的類型。  
  
 *Boxing* 是指將類型轉換為 `Object` 或者，在某些情況下，轉換為 <xref:System.ValueType> 時所需的處理。 Common Language Runtime 無法 box 處理某些類型，例如 <xref:System.ArgIterator> 和 <xref:System.TypedReference>。  
  
 如果您未在包含此運算式的陳述式中搭配使用 `CType` 或 `CObj`，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 嘗試造成此錯誤的隱含轉換。  
  
 **錯誤 ID︰**BC31394  
  
### 更正這個錯誤  
  
1.  找出評估至所指出類型的運算式。  
  
2.  找出嘗試對所指出類型進行 box 處理的陳述式部分。  
  
3.  重寫陳述式，以避免 boxing 轉換。  
  
## 請參閱  
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)