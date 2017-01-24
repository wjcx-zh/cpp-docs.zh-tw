---
title: "類型參數 &#39;&lt;類型參數名稱&gt;&#39; 與封入類型的類型參數擁有相同的名稱 | Microsoft Docs"
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
  - "vbc40048"
  - "bc40048"
helpviewer_keywords: 
  - "BC40048"
ms.assetid: d5428b36-88d3-42c4-a096-cbc7bb9571f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數 &#39;&lt;類型參數名稱&gt;&#39; 與封入類型的類型參數擁有相同的名稱
泛型類型的類型參數宣告成與包含泛型類型的類型參數同名。  
  
 在泛型類型的類型參數清單中，每個類型參數的名稱必須與下列所有名稱不同：  
  
-   相同類型參數清單中的所有其他類型參數、  
  
-   任何包含泛型類型的類型參數清單中的每個類型參數，以及  
  
-   泛型類型本身的名稱。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40048  
  
### 更正這個錯誤  
  
-   重新命名類型參數，使其與這個 \[說明\] 頁面之清單中所指出的每個名稱不同。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)