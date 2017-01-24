---
title: "類型參數不可以與其定義函式同名 | Microsoft Docs"
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
  - "vbc32090"
  - "bc32090"
helpviewer_keywords: 
  - "BC32090"
ms.assetid: 02f4d82c-dcd7-44cc-b725-81e235f680f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數不可以與其定義函式同名
泛型類型的類型參數宣告成與泛型類型同名。  
  
 在泛型類型的類型參數清單中，每個類型參數的名稱必須與下列所有名稱不同：  
  
-   相同類型參數清單中的所有其他類型參數、  
  
-   任何包含泛型類型的類型參數清單中的每個類型參數，以及  
  
-   泛型類型本身的名稱。  
  
 **錯誤 ID：**BC32090  
  
### 更正這個錯誤  
  
-   重新命名類型參數，使其與這個 \[說明\] 頁面之清單中所指出的每個名稱不同。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)