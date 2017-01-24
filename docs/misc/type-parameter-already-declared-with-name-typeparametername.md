---
title: "類型參數已使用名稱 &#39;&lt;類型參數名稱&gt;&#39; 進行宣告。 | Microsoft Docs"
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
  - "vbc32049"
  - "bc32049"
helpviewer_keywords: 
  - "BC32049"
ms.assetid: d7affad0-0c3d-4fce-a1c2-a17f65514471
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數已使用名稱 &#39;&lt;類型參數名稱&gt;&#39; 進行宣告。
泛型類型的類型參數宣告成與相同泛型類型的另一個類型參數同名。  
  
 在泛型類型的類型參數清單中，每個類型參數的名稱必須與下列所有名稱不同：  
  
-   相同類型參數清單中的所有其他類型參數、  
  
-   任何包含泛型類型的類型參數清單中的每個類型參數，以及  
  
-   泛型類型本身的名稱。  
  
 **錯誤 ID︰**BC32049  
  
### 更正這個錯誤  
  
-   重新命名類型參數，使其與這個 \[說明\] 頁面之清單中所指出的每個名稱不同。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)