---
title: "&#39;ReDim&#39; 無法變更維度的數目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArray_RankMismatch"
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; 無法變更維度的數目
作業嘗試使用 `ReDim` 陳述式變更陣列的陣序 \(維度數目\)。`ReDim` 可以變更已正式宣告之陣列的一或多個維度大小，但無法變更陣列的陣序。  
  
### 更正這個錯誤  
  
-   請確定您是要變更陣列的陣序，而不是其維度的大小，並且請盡可能地使用 `Dim` 來宣告具有所需陣序的新陣列。  
  
## 請參閱  
 [NOTINBUILD Visual Basic 中的陣列概觀](http://msdn.microsoft.com/zh-tw/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD Visual Basic 中的多維陣列](http://msdn.microsoft.com/zh-tw/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)