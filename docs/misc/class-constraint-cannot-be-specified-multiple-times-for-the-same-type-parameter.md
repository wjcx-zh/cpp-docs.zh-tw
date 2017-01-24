---
title: "不能針對相同的類型參數多次指定 &#39;Class&#39; 條件約束 | Microsoft Docs"
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
  - "bc32101"
  - "vbc32101"
helpviewer_keywords: 
  - "BC32101"
ms.assetid: fac2330a-e397-4bd9-8166-934407575f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能針對相同的類型參數多次指定 &#39;Class&#39; 條件約束
條件約束清單多次包含 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 條件約束。  
  
 類型參數的條件約束清單可以指定傳遞至該類型參數的類型引數必須是實值類型 \(使用 [Structure \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 條件約束\)，或必須是參考類型 \(使用 `Class` 條件約束\)。 您無法針對相同的類型參數同時指定兩個條件約束，並且無法多次指定其中一個。  
  
 錯誤 ID︰BC32101  
  
### 更正這個錯誤  
  
-   移除任何多餘的 `Class` 關鍵字。 條件約束清單中只能有一個條件約束。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)