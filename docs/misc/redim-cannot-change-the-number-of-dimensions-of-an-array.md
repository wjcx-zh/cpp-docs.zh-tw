---
title: "&#39;ReDim&#39; 無法變更陣列的維度數目 | Microsoft Docs"
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
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; 無法變更陣列的維度數目
您嘗試使用 `ReDim` 變更陣列的陣序 \(維度數目\)。`ReDim` 陳述式可用來變更已正式宣告之陣列的一或多個維度大小，但無法變更陣列的陣序。  
  
 **錯誤 ID︰**BC30415  
  
### 更正這個錯誤  
  
-   確定您指定陣序，而不是陣列的大小，並盡可能使用 `Dim` 來宣告具有所需陣序的新陣列。  
  
## 請參閱  
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [NOTINBUILD Visual Basic 中的陣列概觀](http://msdn.microsoft.com/zh-tw/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)