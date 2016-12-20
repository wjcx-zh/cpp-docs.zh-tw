---
title: "不可以在這個宣告上指定類型參數 | Microsoft Docs"
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
  - "vbc32065"
  - "bc32065"
helpviewer_keywords: 
  - "BC32065"
ms.assetid: 94cfe3de-74fd-4a2c-9246-ec4a05b73d55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不可以在這個宣告上指定類型參數
程式設計項目是使用類型參數清單所宣告，但程式設計項目不可作為泛型類型。  
  
 不可作為泛型的程式設計項目包含屬性、運算子、事件和建構函式。 使用類別參數清單宣告上述任何項目，都會導致這個錯誤。  
  
 **錯誤 ID︰**BC32065  
  
### 更正這個錯誤  
  
-   請從宣告中移除 `Of` 關鍵字和類型參數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)