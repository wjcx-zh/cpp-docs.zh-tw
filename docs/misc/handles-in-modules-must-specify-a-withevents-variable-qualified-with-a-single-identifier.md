---
title: "模組中的 &#39;Handles&#39; 必須指定以單一識別項限定的 &#39;WithEvents&#39; 變數 | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模組中的 &#39;Handles&#39; 必須指定以單一識別項限定的 &#39;WithEvents&#39; 變數
若要指定事件處理常式，`Handles` 陳述式必須指定以 `WithEvents` 關鍵字宣告的物件變數。  
  
 **錯誤 ID︰**BC31418  
  
### 更正這個錯誤  
  
-   請使用 `WithEvents` 修飾詞來宣告將會搭配 `Handles` 陳述式使用的變數。  
  
## 請參閱  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [WithEvents](../Topic/WithEvents%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)