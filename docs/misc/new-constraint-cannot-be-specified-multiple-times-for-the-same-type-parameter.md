---
title: "不能針對相同的類型參數多次指定 &#39;New&#39; 條件約束 | Microsoft Docs"
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
  - "vbc32081"
  - "BC32081"
helpviewer_keywords: 
  - "BC32081"
ms.assetid: afcb30da-3973-4452-9cf3-c027f9866589
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能針對相同的類型參數多次指定 &#39;New&#39; 條件約束
條件約束清單多次包含 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md) 條件約束。  
  
 類型參數的條件約束清單可以指定傳遞至該類型參數的類型引數必須公開建立程式碼可以存取的無參數建構函式。 類型只能有一個無參數建構函式，而且這個需求只能指定一次。  
  
 **錯誤 ID：**BC32081  
  
### 更正這個錯誤  
  
-   移除任何多餘的 `New` 關鍵字。 條件約束清單中只能有一個條件約束。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)