---
title: "&#39;Using&#39; 資源變數類型不能是陣列類型 | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Using&#39; 資源變數類型不能是陣列類型
`Using` 陳述式指定資源的陣列變數。  
  
 <xref:System.Array> 類別未實作 <xref:System.IDisposable> 介面，因此 `Using` 區塊無法在陣列資源上呼叫 <xref:System.IDisposable.Dispose%2A> 方法。  
  
 **錯誤 ID︰**BC36012  
  
### 更正這個錯誤  
  
-   在 `Using` 區塊中使用不同類型的系統資源。  
  
## 請參閱  
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [NOTINBUILD Visual Basic 中的陣列概觀](http://msdn.microsoft.com/zh-tw/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)