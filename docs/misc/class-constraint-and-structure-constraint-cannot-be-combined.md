---
title: "無法合併 &#39;Class&#39; 條件約束和 &#39;Structure&#39; 條件約束 | Microsoft Docs"
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
  - "vbc32104"
  - "bc32104"
helpviewer_keywords: 
  - "BC32104"
ms.assetid: f41a581b-afca-4173-bc82-b35ed49caba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法合併 &#39;Class&#39; 條件約束和 &#39;Structure&#39; 條件約束
條件約束清單同時包含 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 條件約束和 [Structure \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) 條件約束。  
  
 類型參數的條件約束清單可以指定傳遞至該類型參數的類型引數必須是實值類型 \(使用 `Structure` 條件約束\)，或必須是參考類型 \(使用 `Class` 條件約束\)。 您無法針對相同的類型參數同時指定兩個條件約束，並且無法多次指定其中一個。  
  
 **錯誤 ID︰**BC32104  
  
### 更正這個錯誤  
  
1.  請決定您要針對類型引數要求實值類型或參考類型。  
  
    -   如果您希望類型引數是實值類型，請從條件約束清單中移除 `Class` 關鍵字。  
  
    -   如果您希望類型引數是參考類型，請從條件約束清單中移除 `Structure` 關鍵字。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)