---
title: "類型引數 &#39;&lt;類型引數名稱&gt;&#39; 未滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;Class&#39; 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型引數 &#39;&lt;類型引數名稱&gt;&#39; 未滿足類型參數 &#39;&lt;類型參數名稱&gt;&#39; 的 &#39;Class&#39; 條件約束
提供給泛型類型的類型參數未滿足其對應類型參數的參考類型條件約束。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 如果您未在條件約束清單中包含任何特定類別或介面，則可以指定下列其中一項以強制一般需求：  
  
-   類型引數必須是實值類型 \(包含 [Structure \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 條件約束\)  
  
-   類型引數必須是參考類型 \(包含 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 條件約束\)  
  
 您無法針對相同的類型參數同時指定 `Structure` 和 `Class`，並且無法多次指定其中一個。  
  
 **錯誤 ID︰**BC32106  
  
### 更正這個錯誤  
  
-   選取任何參考類型的類型引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [如何：使用泛型類別](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)