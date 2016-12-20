---
title: "不能針對相同的類型參數多次指定 &#39;Structure&#39; 條件約束 | Microsoft Docs"
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
  - "bc32102"
  - "vbc32102"
helpviewer_keywords: 
  - "BC32102"
ms.assetid: f4ebd416-7fb9-4a24-a8df-e9ee7ccc2c76
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能針對相同的類型參數多次指定 &#39;Structure&#39; 條件約束
條件約束清單多次包含 [Structure \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 條件約束。  
  
 類型參數的條件約束清單可以指定傳遞至該類型參數的類型引數必須是實值類型 \(使用 `Structure` 條件約束\)，或必須是參考類型 \(使用 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 條件約束\)。 您無法針對相同的類型參數同時指定兩個條件約束，並且無法多次指定其中一個。  
  
 錯誤 ID︰BC32102  
  
### 更正這個錯誤  
  
-   移除任何多餘的 `Structure` 關鍵字。 條件約束清單中只能有一個條件約束。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)