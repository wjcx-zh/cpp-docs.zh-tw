---
title: "&#39;ReDim&#39; 只能變更最右側的維度 | Microsoft Docs"
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
  - "vbrArray_TypeMismatch"
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; 只能變更最右側的維度
`ReDim` 陳述式嘗試使用 `Preserve` 關鍵字來變更不是最後一個維度的陣列的維度。 使用 `Preserve` 時，您只能調整陣列的最後一個維度。 對於所有其他維度，您必須指定與現有陣列相同的大小。  
  
### 更正這個錯誤  
  
-   請移除 `Preserve` 關鍵字。  
  
## 請參閱  
 [NOTINBUILD Visual Basic 中的陣列概觀](http://msdn.microsoft.com/zh-tw/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD Visual Basic 中的多維陣列](http://msdn.microsoft.com/zh-tw/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [Preserve \- delete](http://msdn.microsoft.com/zh-tw/91badeab-b4e0-48b6-92c9-9f0c8f995d81)