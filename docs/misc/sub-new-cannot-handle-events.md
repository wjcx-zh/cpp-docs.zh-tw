---
title: "&#39;Sub New&#39; 無法處理事件 | Microsoft Docs"
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
  - "vbc30497"
  - "bc30497"
helpviewer_keywords: 
  - "BC30497"
ms.assetid: b8a546c4-914e-49de-b553-9fc0f41424ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; 無法處理事件
您嘗試結合 `Sub New` 與 `Handles`，這種做法無效。 在程序宣告結尾使用 `Handles` 關鍵字，讓它處理由使用 `WithEvents` 關鍵字宣告之物件變數引發的事件。  
  
 **錯誤 ID︰**BC30497  
  
### 更正這個錯誤  
  
1.  請勿在這個內容中使用 `New`。  
  
## 請參閱  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [WithEvents](../Topic/WithEvents%20\(Visual%20Basic\).md)