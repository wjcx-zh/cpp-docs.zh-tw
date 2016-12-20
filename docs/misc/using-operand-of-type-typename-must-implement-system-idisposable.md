---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 的 &#39;Using&#39; 運算元必須實作 System.IDisposable | Microsoft Docs"
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
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 的 &#39;Using&#39; 運算元必須實作 System.IDisposable
`Using` 陳述式指定的資源類型，不會實作 <xref:System.IDisposable> 介面。  
  
 `Using` 區塊的目的是離開區塊時，保證會處置系統資源。 為了滿足此用途，資源必須公開從 <xref:System.IDisposable> 實作的 <xref:System.IDisposable.Dispose%2A> 方法。  
  
 **錯誤 ID：**BC36010  
  
### 更正這個錯誤  
  
-   從 `Using` 陳述式的資源清單中移除資源，或以實作 <xref:System.IDisposable> 的資源取而代之。  
  
## 請參閱  
 <xref:System.IDisposable>   
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)