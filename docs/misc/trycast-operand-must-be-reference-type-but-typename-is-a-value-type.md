---
title: "&#39;TryCast&#39; 運算元必須為參考類型，但 &#39;&lt;類型名稱&gt;&#39; 是實值類型 | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TryCast&#39; 運算元必須為參考類型，但 &#39;&lt;類型名稱&gt;&#39; 是實值類型
`TryCast` 運算子會與至少一個引數的實值類型搭配使用。  
  
 `TryCast` 會測試兩個引數之間的繼承或實作關聯性。 因此，它僅允許引數的參考類型。 如需詳細資訊，請參閱[Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)。  
  
 **錯誤 ID︰**BC30792  
  
### 更正這個錯誤  
  
-   請使用 `DirectCast` 或 `CType` 來執行轉換。 它們都允許實值類型。  
  
## 請參閱  
 [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)