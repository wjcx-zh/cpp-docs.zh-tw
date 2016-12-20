---
title: "類別中的 &#39;Handles&#39; 必須指定以單一識別項限定的 &#39;WithEvents&#39; 變數、&#39;MyBase&#39;、&#39;MyClass&#39; 或 &#39;Me&#39; | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別中的 &#39;Handles&#39; 必須指定以單一識別項限定的 &#39;WithEvents&#39; 變數、&#39;MyBase&#39;、&#39;MyClass&#39; 或 &#39;Me&#39;
若要指定事件處理常式，`Handles` 陳述式必須指定以 `WithEvents` 關鍵字宣告的物件變數，或以 `MyBase` 關鍵字限定的成員。  
  
 **錯誤 ID：**BC31412  
  
### 更正這個錯誤  
  
1.  請使用 `WithEvents` 修飾詞來宣告將會搭配 `Handles` 陳述式使用的變數。  
  
2.  指定基底類別中目前類別的事件名稱。  
  
## 請參閱  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [WithEvents](../Topic/WithEvents%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)